---
title: sys. dm_pdw_network_credentials （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 87134a4898b0eb5e314aa4c0f860755a9618b4c5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830477"
---
# <a name="sysdm_pdw_network_credentials-transact-sql"></a>sys. dm_pdw_network_credentials （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  返回所有目标服务器在设备中存储的所有网络凭据的列表 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 。 为控制节点和每个计算节点列出结果。  
  
|列名|数据类型|说明|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|与节点关联的唯一数字 id。|  
|target_server_name|**nvarchar(32)**|[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]将使用用户名和密码凭据访问的目标服务器的 IP 地址。|  
|username|**nvarchar(32)**|为其存储密码的用户名。|  
|last_modified|**datetime**|修改凭据的上一个操作的日期时间。|  
  
## <a name="permissions"></a>权限  
 需要 VIEW SERVER STATE。  
  
## <a name="general-remarks"></a>一般备注  
 此动态管理视图的键*pdw_node_id*加*target_server_name*。  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
