---
title: ManufacturingFirstWeekOfMonth 元素 (ASSL) |Microsoft 文档
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ManufacturingFirstWeekOfMonth Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ManufacturingFirstWeekOfMonth
helpviewer_keywords:
- ManufacturingFirstWeekOfMonth element
ms.assetid: adb76a2f-c6c3-459e-a441-e80adad76ff1
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 08cf661e55b10a5272412e97480e7866754edddd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="manufacturingfirstweekofmonth-element-assl"></a>ManufacturingFirstWeekOfMonth 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  定义生产月的第一周[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)元素。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
< TimeBinding>  
   ...  
   <ManufacturingFirstWeekOfMonth>...</ManufacturingFirstWeekOfMonth>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|数据类型和长度|Integer（1 到 4）|  
|默认值|**1**|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|子元素|无|  
  
## <a name="remarks"></a>注释  
 对应于的父元素**ManufacturingFirstWeekOfMonth**在分析管理对象 (AMO) 对象模型并<xref:Microsoft.AnalysisServices.TimeBinding>。  
  
## <a name="see-also"></a>另请参阅  
 [属性 & #40;ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  