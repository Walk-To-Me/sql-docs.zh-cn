---
title: XML 中的记录集动态属性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: rothja
ms.author: jroth
ms.openlocfilehash: d9d19ded093cd10a7670b31cd2d5c78a475950d2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760963"
---
# <a name="recordset-dynamic-properties-in-xml"></a>XML 中的记录集动态属性
以下记录集提供程序特定属性（来自客户端游标引擎）当前已保留为 XML 格式：  
  
-   更新重新同步  
  
-   唯一表  
  
-   唯一架构  
  
-   唯一目录  
  
-   重新同步命令  
  
-   IrowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   调整名称  
  
-   AutoRecalc  
  
 这些属性保存在 schema 节中，作为要保存的记录集的元素定义的属性。 这些属性是在行集架构命名空间中定义的，并且必须具有前缀 "rs："。  
  
## <a name="see-also"></a>另请参阅  
 [以 XML 格式保留记录](../../../ado/guide/data/persisting-records-in-xml-format.md)
