---
title: sp_replcounters （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replcounters
- sp_replcounters_TSQL
helpviewer_keywords:
- sp_replcounters
ms.assetid: fe585b1f-edda-421f-81d6-8a03a3a535d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 859e214a0caccc9e515a5377d707aeb3d29c69da
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833116"
---
# <a name="sp_replcounters-transact-sql"></a>sp_replcounters (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  为每个发布数据库返回有关滞后时间、吞吐量和事务计数的复制统计信息。 此存储过程在发布服务器的任何数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_replcounters  
  
```  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**Database**|**sysname**|数据库的名称。|  
|**Replicated transactions**|**int**|日志中等待传送到分发数据库的事务数。|  
|**Replication rate trans/sec**|**float**|平均每秒传送到分发数据库的事务数。|  
|**复制延迟**|**float**|事务在分发前位于日志中的平均时间（秒）。|  
|**Replbeginlsn**|**binary(10)**|日志中当前截断点的日志序列号 (LSN)。|  
|**Replnextlsn**|**binary(10)**|等待传送到分发数据库的下一个提交记录的 LSN。|  
  
## <a name="remarks"></a>备注  
 **sp_replcounters**用于事务复制。  
  
## <a name="permissions"></a>权限  
 需要**db_owner**固定数据库角色或**sysadmin**固定服务器角色的成员身份。  
  
## <a name="see-also"></a>另请参阅  
 [sp_replcmds &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
