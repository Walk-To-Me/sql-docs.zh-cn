---
title: sys. dm_tran_commit_table （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_tran_commit_table
- dm_tran_commit_table_TSQL
- sys.dm_tran_commit_table
- sys.dm_tran_commit_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_commit_table dynamic management view
ms.assetid: 732d23c5-1f6c-4e96-bc85-8f29b520cf0e
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 84278124664b72c45e038de7981057eaff1014f0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82819761"
---
# <a name="change-tracking---sysdm_tran_commit_table"></a>更改跟踪-sys. dm_tran_commit_table
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  对于为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更改跟踪所跟踪的表所提交的每个事务显示一行。 sys.dm_tran_commit_table 管理视图是为可支持性目的而提供的，它公开由更改跟踪存储在 sys.syscommittab 系统表中的与事务相关的信息。 sys.syscommittab 表提供从数据库特定事务 ID 到该事务的提交日志序列号 (LSN) 和提交时间戳的高效永久映射。 存储于 sys.syscommittab 表中并且在此管理视图中公开的数据将按照在配置更改跟踪时所指定的保留期进行清理。  
  
> [!NOTE]  
>  若要从或调用此 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ，请使用名称**dm_pdw_nodes_tran_commit_table**。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|commit_ts|**bigint**|一个单调递增的编号，充当每个已提交事务的数据库特定时间戳。|  
|xdes_id|**bigint**|事务的数据库特定内部 ID。|  
|commit_lbn|**bigint**|包含事务提交日志记录的日志块的编号。|  
|commit_csn|**bigint**|特定于实例的事务提交序列号。|  
|commit_time|**smalldatetime**|提交事务的时间。|  
|pdw_node_id|**int**|**适用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此分发所在的节点的标识符。|  
  
## <a name="see-also"></a>另请参阅  
 [动态管理视图和函数 &#40;Transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [关于更改跟踪 (SQL Server)](../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
  


