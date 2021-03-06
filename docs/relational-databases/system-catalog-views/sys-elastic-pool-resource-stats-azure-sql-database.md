---
title: sys.elastic_pool_resource_stats
titleSuffix: Azure SQL Database
ms.date: 01/28/2019
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: reference
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
author: CarlRabeler
ms.author: carlrab
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d642c8991a9043249f896d0d9b27fb23acd9632e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829693"
---
# <a name="syselastic_pool_resource_stats-azure-sql-database"></a>sys.elastic_pool_resource_stats（Azure SQL 数据库）
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  返回 SQL 数据库服务器中所有弹性池的资源使用率统计信息。 对于每个弹性池，报告窗口每 15 秒就会提供一行（每分钟四行）。 这包括池中所有数据库的 CPU、IO、日志和存储消耗以及并发的请求/会话利用率。 此数据将保留14天。 
  
||  
|-|  
|**适用**于： [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12。|  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|指示15秒报告间隔的开始时间的 UTC 时间。|  
|**end_time**|**datetime2**|指示15秒报表间隔结束时间的 UTC 时间。|  
|**elastic_pool_name**|**nvarchar(128)**|弹性数据库池的名称。|  
|**avg_cpu_percent**|**decimal （5，2）**|以池的限制百分比形式表示的平均计算使用率。|  
|**avg_data_io_percent**|**decimal （5，2）**|以基于池的限制的百分比形式表示的平均 I/O 使用率。|  
|**avg_log_write_percent**|**decimal （5，2）**|以池的限制百分比形式表示的平均写入资源使用率。|  
|**avg_storage_percent**|**decimal （5，2）**|以池的存储限制百分比形式表示的平均存储使用率。|  
|**max_worker_percent**|**decimal （5，2）**|以基于池的限制的百分比形式表示的最大并发工作线程（请求）数量。|  
|**max_session_percent**|**decimal （5，2）**|以基于池的限制的百分比形式表示的最大并发会话（请求）数量。|  
|**elastic_pool_dtu_limit**|**int**|在该时间间隔内该弹性池的当前最大弹性池 DTU 设置。|  
|**elastic_pool_storage_limit_mb**|**bigint**|在该时间间隔内该弹性池的当前最大弹性池存储限制设置（以兆字节为单位）。|
|**avg_allocated_storage_percent**|**decimal （5，2）**|弹性池中所有数据库分配的数据空间百分比。  这是为弹性池分配的数据空间与数据最大大小的比率。  有关详细信息，请参阅[SQL DB 中的文件空间管理](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|  
  
## <a name="remarks"></a>备注

 此视图存在于 SQL 数据库服务器的 master 数据库中。 您必须连接到 master 数据库才能查询**sys.databases elastic_pool_resource_stats**。  
  
## <a name="permissions"></a>权限

 要求具有**dbmanager**角色的成员身份。  
  
## <a name="examples"></a>示例

 下面的示例返回当前 SQL 数据库服务器中所有弹性数据库池的最近时间排序的资源利用率数据。  
  
```sql
SELECT * FROM sys.elastic_pool_resource_stats
ORDER BY end_time DESC;  
```

 下面的示例计算给定池的平均 DTU 百分比消耗量。  

```sql
SELECT start_time, end_time,
  (SELECT Max(v)
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]
FROM sys.elastic_pool_resource_stats
WHERE elastic_pool_name = '<your pool name>'
ORDER BY end_time DESC;  
```

## <a name="see-also"></a>另请参阅

 [通过弹性数据库应对爆炸性增长](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [创建和管理 SQL 数据库弹性数据库池（预览版）](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [resource_stats &#40;Azure SQL 数据库&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [dm_db_resource_stats &#40;Azure SQL 数据库&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
