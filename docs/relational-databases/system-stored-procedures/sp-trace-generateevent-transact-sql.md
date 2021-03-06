---
title: sp_trace_generateevent （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_generateevent_TSQL
- sp_trace_generateevent
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_generateevent
ms.assetid: 3ef05bfb-b467-4403-89cc-6e77ef9247dd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c5807225c2bda185b61050433cc3378b25b6fe1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82809613"
---
# <a name="sp_trace_generateevent-transact-sql"></a>sp_trace_generateevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建用户定义事件。  
  
>**注意：** **不**推荐使用此存储过程。 不推荐使用所有其他与跟踪相关的存储过程。  
  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_trace_generateevent [ @eventid = ] event_id   
     [ , [ @userinfo = ] 'user_info' ]  
     [ , [ @userdata = ] user_data ]  
```  
  
## <a name="arguments"></a>参数  
`[ @eventid = ] event_id`要打开的事件的 ID。 *event_id*为**int**，没有默认值。 ID 必须是82到91中的事件编号之一，表示用户定义的事件， [sp_trace_setevent](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)设置。  
  
`[ @userinfo = ] 'user_info'`是可选的用户定义的字符串，用于标识事件的原因。 *user_info*的默认值为**nvarchar （128）**，默认值为 NULL。  
  
`[ @userdata = ] user_data`是事件的可选的用户指定数据。 *user_data*为**varbinary （8000）**，默认值为 NULL。  
  
## <a name="return-code-values"></a>返回代码值  
 下表说明在存储过程完成后用户可能获得的代码值。  
  
|返回代码|说明|  
|-----------------|-----------------|  
|**0**|没有错误。|  
|**1**|未知错误。|  
|**3**|指定的事件无效。 该事件可能不存在或者它不适用于此存储过程。|  
|**9**|内存不足。 在没有足够内存执行指定的操作时返回此代码。|  
  
## <a name="remarks"></a>备注  
 **sp_trace_generateevent**执行先前由**xp_trace_ \* **扩展存储过程执行的许多操作。 使用**sp_trace_generateevent**而不是**xp_trace_generate_event**。  
  
 仅用户定义事件的 ID 号可与**sp_trace_generateevent**一起使用。 如果使用其他事件 ID 号，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将产生错误。  
  
 所有 SQL 跟踪存储过程的参数（**sp_trace_xx**）都是严格类型化的。 如果没有用正确的输入参数数据类型（参数说明中指定的类型）来调用这些参数，则存储过程将返回错误。  
  
## <a name="permissions"></a>权限  
 用户必须拥有 ALTER TRACE 权限。  
  
## <a name="examples"></a>示例  
 以下示例对一个示例表创建用户可配置的事件。  
  
```  
--Create a sample table.  
CREATE TABLE user_config_test(col1 int, col2 char(10));  
  
--DROP the trigger if it already exists.  
IF EXISTS  
   (SELECT * FROM sysobjects WHERE name = 'userconfig_trg')  
   DROP TRIGGER userconfig_trg;  
  
--Create an ON INSERT trigger on the sample table.  
CREATE TRIGGER userconfig_trg  
   ON user_config_test FOR INSERT;  
AS  
EXEC master..sp_trace_generateevent  
   @event_class = 82, @userinfo = N'Inserted row into user_config_test';  
  
--When an insert action happens, the user-configurable event fires. If   
you were capturing the event id=82, you will see it in the Profiler output.  
INSERT INTO user_config_test VALUES(1, 'abc');  
```  
  
## <a name="see-also"></a>另请参阅  
 [sys. fn_trace_geteventinfo &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [SQL 跟踪](../../relational-databases/sql-trace/sql-trace.md)  
  
  
