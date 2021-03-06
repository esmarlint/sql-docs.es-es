---
title: Versión de ejemplo 6.2.2 del almacén de claves de Azure | Documentos de Microsoft
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f51fc5a5dace2c973b363e26d3c5d627a370f1f1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32832370"
---
# <a name="azure-key-vault-sample-version-622"></a>Versión de ejemplo de almacén de claves de Azure 6.2.2
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

##  <a name="sample-application-using-azure-key-vault-feature"></a>Aplicación de ejemplo mediante la característica almacén de claves de Azure
Esta aplicación no es ejecutable mediante el controlador JDBC 6.2.2 y anterior y Azure-Keyvault (versión 1.0.0), Adal4j (versión 1.4.0) y sus dependencias.  Las dependencias subyacentes pueden resolverse mediante la adición de estas bibliotecas en el archivo pom del proyecto como se describe [aquí](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md): 

```xml
import java.net.URISyntaxException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.HashMap;
import java.util.Map;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionAzureKeyVaultProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerConnection;
import com.microsoft.sqlserver.jdbc.SQLServerException;

public class AE_AKV_Maven {

    private static String connectionUrl = "jdbc:sqlserver://localhost;integratedSecurity=true;database=test;columnEncryptionSetting=enabled";
    static String applicationClientID = "Your Client ID"; 
    static String applicationKey = "Your Application Key";
    static String keyID = "Your Key ID"; 
    static String cmkName = "AKV_CMK_JDBC";
    static String cekName = "AKV_CEK_JDBC";
    static String akvTable = "akvTable";

    static String createTableSQL = "create table " + akvTable + " (" + "PlainNvarcharMax nvarchar(max) null,"
            + "RandomizedNvarcharMax nvarchar(max) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', COLUMN_ENCRYPTION_KEY = "
            + cekName + ") NULL,"
            + "DeterministicNvarcharMax nvarchar(max) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', COLUMN_ENCRYPTION_KEY = "
            + cekName + ") NULL" + ");";

    public static void main(String[] args) throws ClassNotFoundException, Exception {
        Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
        try (Connection connection = DriverManager.getConnection(connectionUrl);
                Statement statement = connection.createStatement()) {

             statement.execute("DBCC FREEPROCCACHE");

             SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new
             SQLServerColumnEncryptionAzureKeyVaultProvider(applicationClientID,
             applicationKey);

            setupKeyStoreProviders(akvProvider.getName(), akvProvider);

            testAKV(akvProvider.getName(), akvProvider, statement);

            connection.close();
        }
    }

    private static void testAKV(String CUSTOM_AKV_PROVIDER_NAME, SQLServerColumnEncryptionKeyStoreProvider akvProvider,
            Statement statement) throws SQLException, SQLServerException, InterruptedException {

        dropTable(statement);

        dropKeys(statement);

        System.out.println("createCMK");
        createCMK(CUSTOM_AKV_PROVIDER_NAME, statement);

        System.out.println("createCEK");
        createCEK(akvProvider, statement);

        System.out.println("create Table");
        statement.execute(createTableSQL);

        System.out.println("populate");
        populateCharNormalCase();

        System.out.println("test");
        testChar();
    }

    /**
     * Sets up keystore
     * 
     * @param CUSTOM_AKV_PROVIDER_NAME
     * @param akvProvider
     * @throws SQLServerException
     */
    private static void setupKeyStoreProviders(String CUSTOM_AKV_PROVIDER_NAME,
            SQLServerColumnEncryptionKeyStoreProvider akvProvider) throws SQLServerException {
        Map<String, SQLServerColumnEncryptionKeyStoreProvider> map1 = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
        map1.put(CUSTOM_AKV_PROVIDER_NAME, akvProvider);
        SQLServerConnection.registerColumnEncryptionKeyStoreProviders(map1);
    }

    /**
     * Cleans and drops tables
     * 
     * @throws SQLException
     */
    private static void dropTable(Statement statement) throws SQLException {
        statement.executeUpdate("if object_id('" + akvTable + "','U') is not null" + " drop table " + akvTable);
    }

    /**
     * Drops CMKs and CEKs
     * 
     * @throws SQLException
     */
    private static void dropKeys(Statement statement) throws SQLException {
        statement.executeUpdate("if exists (SELECT name from sys.column_encryption_keys where name='" + cekName + "')"
                + " begin" + " drop column encryption key " + cekName + " end");

        statement.executeUpdate("if exists (SELECT name from sys.column_master_keys where name='" + cmkName + "')"
                + " begin" + " drop column master key " + cmkName + " end");
    }

    /**
     * Creates CMK using the keystore
     * 
     * @param CUSTOM_AKV_PROVIDER_NAME
     * @throws SQLException
     */
    private static void createCMK(String CUSTOM_AKV_PROVIDER_NAME, Statement statement) throws SQLException {
        String _createColumnMasterKeyTemplate = String.format(
                "CREATE COLUMN MASTER KEY [%s] WITH ( KEY_STORE_PROVIDER_NAME = '%s', KEY_PATH = '%s');", cmkName,
                CUSTOM_AKV_PROVIDER_NAME, keyID);
        statement.execute(_createColumnMasterKeyTemplate);
    }

    /**
     * Creates CEK
     * 
     * @param storeProvider
     * @throws SQLServerException
     * @throws SQLException
     */
    private static void createCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider, Statement statement)
            throws SQLServerException, SQLException {

        String letters = "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa";
        byte[] valuesDefault = letters.getBytes();

        byte[] key = storeProvider.encryptColumnEncryptionKey(keyID, "RSA_OAEP", valuesDefault);

        String cekSql = "CREATE COLUMN ENCRYPTION KEY " + cekName + " WITH VALUES " + "(COLUMN_MASTER_KEY = " + cmkName
                + ", ALGORITHM = 'RSA_OAEP', ENCRYPTED_VALUE = 0x" + bytesToHexString(key, key.length) + ")" + ";";

        statement.execute(cekSql);

    }

    /**
     * 
     * @param b
     *            byte value
     * @param length
     *            length of the array
     * @return
     */
    final static char[] hexChars = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F' };

    private static String bytesToHexString(byte[] b, int length) {
        StringBuilder sb = new StringBuilder(length * 2);
        for (int i = 0; i < length; i++) {
            int hexVal = b[i] & 0xFF;
            sb.append(hexChars[(hexVal & 0xF0) >> 4]);
            sb.append(hexChars[(hexVal & 0x0F)]);
        }
        return sb.toString();
    }

    /**
     * Populates the table
     * 
     * @throws SQLException
     */
    private static void populateCharNormalCase() throws SQLException {
        String sql = "insert into " + akvTable + " values(?,?,?)";
        try (Connection connection = DriverManager.getConnection(connectionUrl);
                PreparedStatement pstmt = connection.prepareStatement(sql)) {

            for (int i = 1; i <= 3; i++) {
                pstmt.setNString(i, "hello world");
            }

            pstmt.execute();
        }
    }

    /**
     * Rerieves the table
     * 
     * @throws SQLException
     */
    private static void testChar() throws SQLException {
        try (Connection connection = DriverManager.getConnection(connectionUrl);
                ResultSet rs = connection.createStatement().executeQuery("select * from " + akvTable);) {
            int numberOfColumns = rs.getMetaData().getColumnCount();

            while (rs.next()) {
                testGetString(rs, numberOfColumns);
            }

        }
    }

    /**
     * Tests the values
     * 
     * @param rs
     * @param numberOfColumns
     * @throws SQLException
     */
    private static void testGetString(ResultSet rs, int numberOfColumns) throws SQLException {
        for (int i = 1; i <= numberOfColumns; i = i + 3) {
            String stringValue1 = "" + rs.getString(i);
            String stringValue2 = "" + rs.getString(i + 1);
            String stringValue3 = "" + rs.getString(i + 2);

            System.out.println(stringValue1);
            System.out.println(stringValue2);
            System.out.println(stringValue3);
        }
    }

}


```

## <a name="see-also"></a>Vea también  
 [Ejemplo de almacén de claves de Azure versión 6.0.0](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md)  