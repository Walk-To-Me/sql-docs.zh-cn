---
title: sp_getbindtoken （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_getbindtoken
- sp_getbindtoken_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_getbindtoken
ms.assetid: 5db87d77-85fa-45a3-a23a-3ea500f9a5ac
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dca4015832f8bebf5501c4b3a7e84339bf62957b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833190"
---
# <a name="sp_getbindtoken-transact-sql"></a>sp_getbindtoken (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回事务的唯一标识符。 该唯一标识符是一个字符串，用来使用 sp_bindsession 绑定会话。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 请改用多个活动结果集 (MARS) 或分布式事务。 有关详细信息，请参阅[使用多个活动的结果集 (MARS)](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_getbindtoken [@out_token =] 'return_value' OUTPUT   
```  
  
## <a name="arguments"></a>参数  
 [ @out_token =] "*return_value*"  
 用于绑定会话的令牌。 *return_value*的值为**varchar （255）** ，无默认值。  
  
## <a name="return-code-values"></a>返回代码值  
 无  
  
## <a name="result-sets"></a>结果集  
 无  
  
## <a name="remarks"></a>备注  
 仅当在活动事务中执行存储过程时，sp_getbindtoken 才会返回有效的令牌。 否则，[!INCLUDE[ssDE](../../includes/ssde-md.md)]将返回错误消息。 例如：  
  
```  
-- Declare a variable to hold the bind token.  
-- No active transaction.  
DECLARE @bind_token varchar(255);  
-- Trying to get the bind token returns an error 3921.  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
Server: Msg 3921, Level 16, State 1, Procedure sp_getbindtoken, Line 4  
Cannot get a transaction token if there is no transaction active.  
Reissue the statement after a transaction has been started.  
```  
  
 当 sp_getbindtoken 用于在打开的事务内登记分布式事务连接时，将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回相同的令牌。 例如：  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @bind_token varchar(255);  
  
BEGIN TRAN;  
  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
  
BEGIN DISTRIBUTED TRAN;  
  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
```  
  
 两个 `SELECT` 语句都返回同一个令牌：  
  
```  
Token  
-----  
PKb'gN5<9aGEedk_16>8U=5---/5G=--  
(1 row(s_) affected)  
  
Token  
-----  
PKb'gN5<9aGEedk_16>8U=5---/5G=--  
(1 row(s_) affected)  
```  
  
 绑定令牌可以与 sp_bindsession 一起使用，将新会话绑定到同一事务上。 绑定令牌仅在每个[!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的本地有效，不能由多个实例共享。  
  
 若要获得并传递绑定令牌，则必须在运行 sp_bindsession 之前运行 sp_getbindtoken，以共享同一锁空间。 如果获得绑定令牌，则 sp_bindsession 可正确运行。  
  
> [!NOTE]  
>  建议使用 srv_getbindtoken 开放式数据服务应用程序编程接口 (API) 来从扩展存储过程获得要使用的绑定令牌。  
  
## <a name="permissions"></a>权限  
 要求具有 public 角色的成员身份。  
  
## <a name="examples"></a>示例  
 下面的示例将获取一个绑定令牌并显示该绑定令牌的名称。  
  
```  
DECLARE @bind_token varchar(255);  
BEGIN TRAN;  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Token`  
  
 `----------------------------------------------------------`  
  
 `\0]---5^PJK51bP<1F<-7U-]ANZ`  
  
## <a name="see-also"></a>另请参阅  
 [sp_bindsession &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [&#40;Transact-sql&#41;系统存储过程](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [扩展存储过程 API srv_getbindtoken &#40;&#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)  
  
  
