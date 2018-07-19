---
title: ad hoc distributed queries 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2451cdb31019da9c21efabec216fdf24b7c71bbe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286033"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a>即席分布式查询服务器配置选项
  默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允许使用 OPENROWSET 和 OPENDATASOURCE 进行即席分布式查询。 此选项设置为 1 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许进行即席访问。 如果此选项未设置或设置为 0，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允许进行即席访问。  
  
 即席分布式查询使用 OPENROWSET 和 OPENDATASOURCE 函数连接到使用 OLE DB 的远程数据源。 OPENROWSET 和 OPENDATASOURCE 只应在引用不常访问的 OLE DB 数据源时使用。 对于将要经常访问的数据源，应定义链接服务器。  
  
> [!IMPORTANT]  
>  允许使用临时名称意味着到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的任何经过身份验证的登录名均可访问该访问接口。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理员应对任何本地登录名都能安全访问的访问接口启用此功能。  
  
## <a name="remarks"></a>Remarks  
 尝试进行即席连接但未启用“ 即席分布式查询 ”  会导致错误：消息 7415，级别 16，状态 1，行 1  
  
 已拒绝对 OLE DB 访问接口“Microsoft.ACE.OLEDB.12.0”的即席访问。 必须通过链接服务器来访问此访问接口。  
  
## <a name="examples"></a>示例  
 下面的示例启用即席分布式查询，然后使用 `Seattle1` 函数查询名为 `OPENROWSET` 的服务器。  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)   
 [链接服务器（数据库引擎）](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [OPENDATASOURCE (Transact-SQL)](/sql/t-sql/functions/opendatasource-transact-sql)   
 [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
  