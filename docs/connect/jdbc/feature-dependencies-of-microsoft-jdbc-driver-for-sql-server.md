---
title: Microsoft JDBC 驱动程序的功能依赖项
description: 了解 Microsoft JDBC Driver for SQL Server 的依赖项，以及如何满足这些依赖项。
ms.custom: ''
ms.date: 03/24/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a08c60322ba4cb75bef804eafb9a3e68e7df5de
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631197"
---
# <a name="feature-dependencies-of-the-microsoft-jdbc-driver-for-sql-server"></a>Microsoft JDBC Driver for SQL Server 的功能依赖项

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

本文列出了 Microsoft JDBC Driver for SQL Server 所依赖的库。 项目具有以下依赖项。

## <a name="compile-time"></a>编译时间

 - `com.microsoft.azure:azure-keyvault`：具有 Always Encrypted Azure Key Vault 功能的 Azure Key Vault 提供程序。 （可选）
 - `com.microsoft.azure:adal4j`：具有 Azure Active Directory 身份验证功能和 Azure Key Vault 功能的用于 Java 的 Azure Active Directory 库。 （可选）
 - `com.microsoft.rest:client-runtime`：具有 Azure Active Directory 身份验证功能和 Azure Key Vault 功能的用于 Java 的 Azure Active Directory 库。 （可选）
 - `org.antlr:antlr4-runtime`设置用户帐户 ：具有 useFmtOnly 功能的 ANTLR 4 Runtime。 （可选）
 - `org.osgi:org.osgi.core`设置用户帐户 ：具有 OSGi Framework 支持的 OSGi Core 库。
 - `org.osgi:org.osgi.compendium`设置用户帐户 ：具有 OSGi Framework 支持的 OSGi Compendium 库。
 - `com.google.code.gson`设置用户帐户 ：具有安全 Enclave 功能的 Always Encrypted 的 JSON 分析器。 （可选）
 - `org.bouncycastle.bcprov-jdk15on`设置用户帐户 ：具有安全 Enclave 功能的 Always Encrypted 的 Bouncy Castle 提供程序（仅当使用 JAVA 8 时）。 （可选）

## <a name="test-time"></a>测试时间

需要任何上述功能的特定项目需要显式声明其 POM 文件中的相应依赖项。

例如：  使用 Azure Active Directory 身份验证功能时，需要重新声明项目的 POM 文件中的 `adal4j` 依赖项。 请查看以下代码片段：

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.2.2.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.4</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.7.0</version>
</dependency>
```

例如：  使用 Azure Key Vault 功能时，需要重新声明 `azure-keyvault` 依赖项和项目的 POM 文件中的 `adal4j` 依赖项。 请查看以下代码片段：

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.2.2.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.4</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.7.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.2.2</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>JDBC 驱动程序的依赖项要求

### <a name="working-with-the-azure-key-vault-provider"></a>使用 Azure Key Vault 提供程序：

- JDBC Driver 版本 8.2.2 - 依赖项版本：Azure-Keyvault（版本 1.2.2）、Adal4j（版本 1.6.4）、Client-Runtime-for-AutoRest (1.7.0) 及其依赖项（[示例应用程序](azure-key-vault-sample-version-7.0.md)）
- JDBC 驱动程序版本 7.4.1 - 依赖项版本：Azure-Keyvault（版本 1.2.1）、Adal4j（版本 1.6.4）、Client-Runtime-for-AutoRest (1.6.10) 及其依赖项（[示例应用程序](azure-key-vault-sample-version-7.0.md)）
- JDBC 驱动程序版本 7.2.2 - 依赖项版本：Azure-Keyvault（版本 1.2.0）、Azure-Keyvault-Webkey（版本 1.2.0）、Adal4j（版本 1.6.3）、Client-Runtime-for-AutoRest (1.6.5) 及其依赖项（[示例应用程序](azure-key-vault-sample-version-7.0.md)）
- JDBC 驱动程序版本 7.0.0 - 依赖项版本：Azure-Keyvault（版本 1.0.0）、Adal4j（版本 1.6.0）及其依赖项（[示例应用程序](azure-key-vault-sample-version-7.0.md)）
- JDBC 驱动程序版本 6.4.0 - 依赖项版本：Azure-Keyvault（版本 1.0.0）、Adal4j（版本 1.4.0）及其依赖项（[示例应用程序](azure-key-vault-sample-version-6.2.2.md)）
- JDBC 驱动程序版本 6.2.2 - 依赖项版本：Azure-Keyvault（版本 1.0.0）、Adal4j（版本 1.4.0）及其依赖项（[示例应用程序](azure-key-vault-sample-version-6.2.2.md)）
- JDBC 驱动程序版本 6.0.0 - 依赖项版本：Azure-Keyvault（版本 0.9.7）、Adal4j（版本 1.3.0）及其依赖项（[示例应用程序](azure-key-vault-sample-version-6.0.0.md)）

> [!NOTE]
> 使用 6.2.2 和 6.4.0 驱动程序版本，azure-keyvault-java 依赖项已更新为版本 1.0.0。 但是，新版本与上一版本 (0.9.7) 不兼容，并且会中断驱动程序中的现有实现。 驱动程序中的新实现需要 API 更改，因而会中断使用 Azure Key Vault 提供程序的客户端程序。
>
> 最新驱动程序版本（7.0.0 以后）可解决此问题。 使用了身份验证回调机制的已删除构造函数将重新添加到 Azure Key Vault 提供程序以进行向后兼容。

### <a name="working-with-azure-active-directory-authentication"></a>使用 Azure Active Directory 身份验证：

- JDBC Driver 版本 8.2.2 - 依赖项版本：Adal4j（版本 1.6.4）、Client-Runtime-for-AutoRest (1.7.0) 及其依赖项。 在此版本的驱动程序中，“sqljdbc_auth”已被重命名为“mssql-jdbc_auth-\<version>-\<arch>.dll”。
- JDBC 驱动程序版本 7.4.1 - 依赖项版本：Adal4j（版本 1.6.4）、Client-Runtime-for-AutoRest (1.6.10) 及其依赖项
- JDBC 驱动程序版本 7.2.2 - 依赖项版本：Adal4j（版本 1.6.3）、Client-Runtime-for-AutoRest (1.6.5) 及其依赖项
- JDBC 驱动程序版本 7.0.0 - 依赖项版本：Adal4j（版本 1.6.0）及其依赖项
- JDBC 驱动程序版本 6.4.0 - 依赖项版本：Adal4j（版本 1.4.0）及其依赖项
- JDBC 驱动程序版本 6.2.2 - 依赖项版本：Adal4j（版本 1.4.0）及其依赖项
- JDBC 驱动程序版本 6.0.0 - 依赖项版本：Adal4j（版本 1.3.0）及其依赖项。 在此版本的驱动程序中，可以仅在 Windows 操作系统上使用 ActiveDirectoryIntegrated  身份验证模式并使用 sqljdbc_auth.dll 和适用于 SQL Server 的 Active Directory 身份验证库 (ADALSQL.DLL) 进行连接。

从驱动程序版本 6.4.0 开始，应用程序不一定需要在 Windows 操作系统上使用 ADALSQL.DLL。 对于非 Windows 操作系统  ，驱动程序需要使用 Kerberos 票证才能进行 ActiveDirectoryIntegrated 身份验证。 若要详细了解如何使用 Kerberos 连接到 Active Directory，请参阅[在 Windows、Linux 和 macOS 上设置 Kerberos 票证](connecting-using-azure-active-directory-authentication.md#set-kerberos-ticket-on-windows-linux-and-macos)。

对于 Windows 操作系统  ，驱动程序默认查找 sqljdbc_auth.dll，并且不需要 Kerberos 票证设置或 Azure 库依赖项。 如果 sqljdbc_auth.dll 不可用，驱动程序会查找用于在其他操作系统上对 Active Directory 进行身份验证的 Kerberos 票证。

从驱动程序版本 8.2.2 开始，“sqljdbc_auth”将被重命名为“mssql-jdbc_auth-\<version>-\<arch>.dll”。 例如 “mssql-jdbc_auth-8.2.2.x64.dll”。

可以获取使用此功能的[示例应用程序](connecting-using-azure-active-directory-authentication.md)。

## <a name="see-also"></a>另请参阅

[JDBC 驱动程序 GitHub 存储库](https://github.com/microsoft/mssql-jdbc)  
[JDBC Driver API 参考](reference/jdbc-driver-api-reference.md)
