---
title: '&gt;= （大于或等于）（DMX） |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3615dc8b5de0e5057e2dedaa0077aae51ed87ebe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "68074792"
---
# <a name="gt-greater-than-or-equal-to-dmx"></a>&gt;= （大于或等于）（DMX）
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  执行比较运算，以确定一个数据挖掘扩展插件 (DMX) 表达式的值是否大于等于另一个 DMX 表达式的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
DMX_Expression >= DMX_Expression  
```  
  
#### <a name="parameters"></a>参数  
 *DMX_Expression*  
 一个有效的 DMX 表达式。  
  
## <a name="return-value"></a>返回值  
 如果两个参数都为非空值，并且第一个参数的值大于或等于第二个参数的值，则返回包含 TRUE 的布尔值。 如果两个参数都为非空值，并且第一个参数的值小于第二个参数的值，则返回包含 FALSE 的布尔值。 如果其中一个参数的计算结果为空值或这两个参数的计算结果均为空值，则该布尔值包含空值。  
  
## <a name="see-also"></a>另请参阅  
 [比较运算符 &#40;DMX&#41;](../dmx/operators-comparison.md)   
 [数据挖掘扩展插件 &#40;DMX&#41; 运算符引用](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [运算符 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
