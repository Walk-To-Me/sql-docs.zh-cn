---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f137d859fa6f6233e14bc34c6bf50797a4360a98
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2020
ms.locfileid: "68123294"
---
# <a name="mssqlserver_41333"></a>MSSQLSERVER_41333
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件 ID|41333|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|CROSS_CONTAINER_ISOLATION_FAILURE|  
|消息正文|以下事务必须在快照隔离下访问内存优化表和本机编译存储过程：RepeatableRead 事务、Serializable 事务以及在 RepeatableRead 或 Serializable 隔离中访问非内存优化表的事务。|  
  
## <a name="explanation"></a>说明  
对于基于磁盘的事务和 XTP 事务之间的更高隔离级别用户，存在一些限制。  
  
## <a name="user-action"></a>用户操作  
不要尝试对内存优化表（和本机编译存储过程）以及基于磁盘的表执行高级别隔离操作。  
  
有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  
## <a name="see-also"></a>另请参阅  
[内存中 OLTP（内存中优化）](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
