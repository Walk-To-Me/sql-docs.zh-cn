---
title: dbo. sysjobhistory （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/24/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobhistory_TSQL
- dbo.sysjobhistory
- sysjobhistory
- sysjobhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobhistory system table
ms.assetid: 1b1fcdbb-2af2-45e6-bf3f-e8279432ce13
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2ff3c872b195123608c12515fb3c19a03c3e3f44
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82807021"
---
# <a name="dbosysjobhistory-transact-sql"></a>dbo.sysjobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

包含有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理执行预定作业的信息。
  
> [!NOTE]
> 在大多数情况下，仅在作业步骤完成并且表通常不包含当前正在进行的作业步骤的记录时才更新数据，但在某些情况下，基础*进程会*提供有关正在进行的作业步骤的信息。

该表存储在**msdb**数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|行的唯一标识符。|  
|**job_id**|**uniqueidentifier**|作业 ID。|  
|**step_id**|**int**|作业中步骤的 ID。|  
|**step_name**|**sysname**|步骤的名称。|  
|**sql_message_id**|**int**|作业失败时返回的任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误消息的 ID。|  
|**sql_severity**|**int**|任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误的严重级别。|  
|**message**|**nvarchar(4000)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误的文本（如果有）。|  
|**run_status**|**int**|作业的执行状态：<br /><br /> **0** = 失败<br /><br /> **1** = 成功<br /><br /> **2** = 重试<br /><br /> **3** = 已取消<br /><br />**4** = 正在进行|  
|**run_date**|**int**|作业或步骤开始执行的日期。 对于正在进行中的历史记录，这是写入历史记录的日期/时间。|  
|**run_time**|**int**|作业或步骤的开始时间，格式为**HHMMSS** 。|  
|**run_duration**|**int**|执行作业或步骤所用的时间（采用**HHMMSS**格式）。|  
|**operator_id_emailed**|**int**|作业完成时通知的操作员的 ID。|  
|**operator_id_netsent**|**int**|作业完成时用消息通知的操作员的 ID。|  
|**operator_id_paged**|**int**|作业完成时用寻呼通知的操作员的 ID。|  
|**retries_attempted**|**int**|尝试执行作业或步骤的重试次数。|  
|**服务**|**sysname**|执行作业时所在服务器的名称。|  
  
  ## <a name="example"></a>示例
 下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询将**run_time**和**run_duration**列转换为更加用户友好格式。  在中执行脚本 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。
 
 ```sql
 SET NOCOUNT ON;
 
 SELECT sj.name,
        sh.run_date,
        sh.step_name,
        STUFF(STUFF(RIGHT(REPLICATE('0', 6) +  CAST(sh.run_time as varchar(6)), 6), 3, 0, ':'), 6, 0, ':') 'run_time',
        STUFF(STUFF(STUFF(RIGHT(REPLICATE('0', 8) + CAST(sh.run_duration as varchar(8)), 8), 3, 0, ':'), 6, 0, ':'), 9, 0, ':') 'run_duration (DD:HH:MM:SS)  '
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobhistory sh
ON sj.job_id = sh.job_id
```
