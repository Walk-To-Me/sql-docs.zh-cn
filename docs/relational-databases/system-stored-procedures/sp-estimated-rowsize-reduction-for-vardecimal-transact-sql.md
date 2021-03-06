---
title: sp_estimated_rowsize_reduction_for_vardecimal （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- sp_estimated_rowsize_reduction_for_vardecimal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- decimal data type, compressing
- numeric data type, compressing
- estimate decimal compression
- table compression [SQL Server]
ms.assetid: 0fe45983-f9f2-4c7f-938a-0fd96e1cbe8d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 292bd66b8c30cec9bc55442a3ab768dd23b731ff
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831067"
---
# <a name="sp_estimated_rowsize_reduction_for_vardecimal-transact-sql"></a>sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  估计对表启用 vardecimal 存储格式后行平均大小的减少量。 使用该数字可估计表大小的总体减少量。 由于使用统计采样来计算行大小的平均减少量，因此只能将该计算结果视为估计值。 在极个别的情况下，启用 vardecimal 存储格式后行大小可能会增加。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]请改用 ROW 和 PAGE 压缩。 有关详细信息，请参阅 [Data Compression](../../relational-databases/data-compression/data-compression.md)。 有关表和索引的大小的压缩效果，请参阅[&#40;transact-sql&#41;sp_estimate_data_compression_savings ](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md)。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_estimated_rowsize_reduction_for_vardecimal [ [ @table_name = ] 'table'] [;]  
```  
  
## <a name="arguments"></a>参数  
`[ @table = ] 'table'`要更改其存储格式的表的三部分名称。 *table*为**nvarchar （776）**。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
 将返回如下结果集，以提供当前表大小和估计表大小的信息。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**avg_rowlen_fixed_format**|**decimal （12，2）**|以固定十进制存储格式表示行的长度。|  
|**avg_rowlen_vardecimal_format**|**decimal （12，2）**|表示使用 vardecimal 存储格式时的平均行大小。|  
|**row_count**|**int**|表中的行数。|  
  
## <a name="remarks"></a>备注  
 使用**sp_estimated_rowsize_reduction_for_vardecimal**估算为 vardecimal 存储格式启用表时产生的节省。 例如，如果平均行大小能够减少 40%，则可能可以将表的大小减少 40%。 您可能无法节省空间，具体取决于填充因子和行大小。 例如，如果某行长度为 8000 字节并且您将该行的大小减少 40%，则数据页上仍只能容纳一行，因而并未节省空间。  
  
 如果**sp_estimated_rowsize_reduction_for_vardecimal**的结果指示表将增长，则表示表中的许多行使用的是 decimal 数据类型的几乎全部精度，而添加 vardecimal 存储格式所需的少量开销大于从 vardecimal 存储格式中节省的费用。 在这种极个别的情况下，不要启用 vardecimal 存储格式。  
  
 如果对表启用了 vardecimal 存储格式，请使用**sp_estimated_rowsize_reduction_for_vardecimal**来估算在禁用 vardecimal 存储格式的情况下行的平均大小。  
  
## <a name="permissions"></a>权限  
 需要对表具有 CONTROL 权限。  
  
## <a name="examples"></a>示例  
 下例估计了 `Production.WorkOrderRouting` 数据库中的 `AdventureWorks2012` 表在压缩后行大小变小的情况。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimated_rowsize_reduction_for_vardecimal 'Production.WorkOrderRouting' ;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [sp_db_vardecimal_storage_format &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)   
 [sp_tableoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
