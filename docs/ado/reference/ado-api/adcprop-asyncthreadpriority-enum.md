---
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
author: rothja
ms.author: jroth
ms.openlocfilehash: ecdc80a2f1e1ace36170a9b4527ba01f0b02ee11
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760653"
---
# <a name="adcprop_asyncthreadpriority_enum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
对于 RDS[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象，指定检索数据的异步线程的执行优先级。  
  
 将这些常量用于**记录集**"**后台线程优先级**" 动态属性，该属性在 ADO 到 OLE DB 的动态属性索引中进行了引用，并在[Microsoft Cursor Service for OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)文档中进行了介绍。  
  
|返回的常量|值|说明|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|设置正常和最高的优先级。|  
|**adPriorityBelowNormal**|2|设置最低和普通的优先级。|  
|**adPriorityHighest**|5|将优先级设置为可能的最高级别。|  
|**AdPriorityLowest**|1|设置尽可能低的优先级。|  
|**adPriorityNormal**|3|将优先级设置为 normal。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 Package： **.com. 数据**  
  
|返回的常量|  
|--------------|  
|AdoEnums. AdcPropAsyncThreadPriority. ABOVENORMAL|  
|AdoEnums. AdcPropAsyncThreadPriority. BELOWNORMAL|  
|AdoEnums. AdcPropAsyncThreadPriority|  
|AdoEnums. AdcPropAsyncThreadPriority|  
|AdoEnums. AdcPropAsyncThreadPriority. NORMAL|
