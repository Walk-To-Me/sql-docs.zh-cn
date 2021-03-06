---
title: sp_wait_for_database_copy_sync
titleSuffix: Azure SQL Database
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_wait_for_database_copy_sync_TSQL
- sp_wait_for_database_copy_sync
dev_langs:
- TSQL
helpviewer_keywords:
- sp_wait_for_database_copy_sync
ms.assetid: 7068da7f-cb74-47f2-b064-eb076a0d3885
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.custom: seo-dt-2019
ms.openlocfilehash: 931babcaa6e229d6114930bba5f06803aa25f59e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829677"
---
# <a name="active-geo-replication---sp_wait_for_database_copy_sync"></a>活动异地复制-sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  此过程的范围限定为主数据库与辅助数据库之间的 [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] 关系。 调用**sp_wait_for_database_copy_sync**会导致应用程序等待，直到所有提交的事务复制并由活动辅助数据库确认。 仅对主数据库运行**sp_wait_for_database_copy_sync** 。  
  
||  
|-|  
|**适用于**： [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
## <a name="syntax"></a>语法  
  
```  
sp_wait_for_database_copy_sync [ @target_server = ] 'server_name'   
     , [ @target_database = ] 'database_name'  
```  
  
## <a name="arguments"></a>参数  
 [ @target_server = ] 'server_name'  
 承载活动辅助数据库的 SQL Database 服务器的名称。 server_name 为 sysname，无默认值。  
  
 [ @target_database = ] 'database_name'  
 活动辅助数据库的名称。 database_name 为 sysname，没有默认值。  
  
## <a name="return-code-values"></a>返回代码值  
 返回 0 表示成功，返回错误编号表示失败。  
  
 最有可能发生的错误情况如下：  
  
-   缺少服务器名称或数据库名称。  
  
-   找不到指定服务器名称或数据库的链接。  
  
-   失去互连连接。 **sp_wait_for_database_copy_sync**将在连接超时后返回。  
  
## <a name="permissions"></a>权限  
 主数据库中的任何用户均可调用此系统存储过程。 登录名必须是主数据库和活动辅助数据库中的用户。  
  
## <a name="remarks"></a>备注  
 在**sp_wait_for_database_copy_sync**调用之前提交的所有事务都将发送到活动辅助数据库。  
  
## <a name="examples"></a>示例  
 下面的示例调用**sp_wait_for_database_copy_sync** ，以确保将所有事务提交到主数据库 db0，并将其发送到目标服务器 ubfyu5ssyt 上的活动辅助数据库。  
  
```  
USE db0;  
GO  
EXEC sys.sp_wait_for_database_copy_sync @target_server = N'ubfyu5ssyt1', @target_database = N'db0';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [dm_continuous_copy_status &#40;Azure SQL 数据库&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-continuous-copy-status-azure-sql-database.md)   
 [异地复制动态管理视图（Dmv）和函数 &#40;Azure SQL 数据库&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status](../system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)
  
  
