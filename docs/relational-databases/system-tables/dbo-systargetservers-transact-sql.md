---
title: dbo. systargetservers （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6193bdfaaac12d34ed4993b71fd6b5862046384c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82813726"
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  记录此多服务器操作域中当前登记的目标服务器。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|服务器 ID。|  
|server_name |**sysname**|服务器名称。|  
|**location**|**nvarchar(200)**|指定目标服务器的位置。|  
|**time_zone_adjustment**|**int**|与格林尼治标准时间 (GMT) 之间的时差调整量（以小时为单位）。|  
|**enlist_date**|**datetime**|指定目标服务器的登记日期和时间。|  
|**last_poll_date**|**datetime**|指定的目标服务器上一次轮询多服务器的**sysdownloadlist**系统表以运行作业的日期和时间。|  
|**status**|**int**|目标服务器的状态：<br /><br /> **1** = 正常<br /><br /> **2** = 正在等待重新同步<br /><br /> **4** = 可疑脱机|  
|**local_time_at_last_poll**|**datetime**|上一次轮询目标服务器作业操作的日期和时间。|  
|**enlisted_by_nt_user**|**nvarchar （100）**|在目标服务器上执行**sp_msx_enlist**的人员的用户名。|  
|**poll_internal**|**int**|目标服务器为获得新下载指令而轮询主服务器前要经过的秒数。|  
  
  
