---
title: 将 Oracle 架构映射到 SQL Server 架构（OracleToSQL） |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: e375c07ceddc995b599930c14f00710af040d6c0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "68262912"
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>将 Oracle 架构映射到 SQL Server 架构 (OracleToSQL)
在 Oracle 中，每个数据库都有一个或多个架构。 默认情况下，SSMA 将 Oracle 架构中的所有对象迁移[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]到名为的数据库的架构。 但是，你可以自定义 Oracle 架构和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库之间的映射。  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle 和 SQL Server 架构  
Oracle 数据库包含架构。 的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例包含多个数据库，每个数据库都可以有多个架构。  
  
架构的 Oracle 概念映射到数据库的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]概念及其架构。 例如，Oracle 可能有一个名为**HR**的架构。 的实例[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可能有一个名为**HR**的数据库，该数据库中的数据库是架构。 一个架构是**dbo** （或数据库所有者）架构。 默认情况下，Oracle schema **hr**将映射到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库，架构**hr. dbo**。 SSMA 是指作为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]架构的数据库和架构的组合。  
  
您可以修改 Oracle 和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]架构之间的映射。  
  
## <a name="modifying-the-target-database-and-schema"></a>修改目标数据库和架构  
在 SSMA 中，可以将 Oracle 架构映射到任何可用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的架构。  
  
**修改数据库和架构**  
  
1.  在 Oracle 元数据资源管理器中，选择 "**架构**"。  
  
    选择单个数据库、"**架构**" 文件夹或单独的架构时，还可以使用 "**架构映射**" 选项卡。 为所选对象自定义 "**架构映射**" 选项卡中的列表。  
  
2.  在右侧窗格中，单击 "**架构映射**" 选项卡。  
  
    你将看到所有 Oracle 架构的列表，后跟目标值。 此目标以两部分表示法（*数据库*）表示， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]其中你的对象和数据将迁移到其中。  
  
3.  选择包含要更改的映射的行，然后单击 "**修改**"。  
  
    在 "**选择目标架构**" 对话框中，您可以浏览可用目标数据库和架构，或在两部分表示法（数据库架构）的文本框中键入数据库和架构名称，然后单击 **"确定"**。  
  
4.  "**架构映射**" 选项卡上的目标更改。  
  
**映射模式**  
  
-   映射到 SQL Server  
  
您可以将源数据库映射到任何目标数据库。 默认情况下，源数据库映射到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用 SSMA 连接的目标数据库。 如果要映射的目标数据库在上[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]不存在，则系统会提示你提供消息 **"目标[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]元数据中不存在数据库和/或架构。它将在同步过程中创建。是否要继续？ "** 单击“是”。 同样，你可以将架构映射到目标[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库下将在同步过程中创建的非现有架构。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>恢复到默认数据库和架构  
如果自定义 Oracle 架构和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]架构之间的映射，则可以将映射恢复为默认值。  
  
**恢复为默认数据库和架构**  
  
1.  在 "架构映射" 选项卡下，选择任意行，然后单击 "**重置为默认值**" 以还原为默认数据库和架构。  
  
## <a name="next-steps"></a>后续步骤  
如果要分析 Oracle 对象到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]对象的转换，可以[创建转换报表](assessing-oracle-schemas-for-conversion-oracletosql.md)。 否则，你可以[将 Oracle 数据库对象定义转换](converting-oracle-schemas-oracletosql.md)为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]对象定义。  
  
## <a name="see-also"></a>另请参阅  
[连接到 SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[将 Oracle 数据库迁移到 SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
