---
title: 与字段相关的错误信息 |Microsoft 文档
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- field-related errors [ADO]
- errors [ADO], field-related
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7491e713f68ee44cd48bf9c53db013a4424e1d1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="field-related-error-information"></a>与字段相关的错误的信息
如果错误直接相关的字段 — 例如，如果数据丢失或它的错误类型的字段是-你可以通过检查检索有关原因的问题的详细信息**字段**对象的**状态**属性。 此属性已得到增强，提供有关的问题的特定信息。 因此，举例来说，当调用**UpdateBatch**可以检查来确定失败，问题的原因**状态**属性**字段**中每个受影响记录。 属性将包含中的值之一**FieldStatusEnum**常量。 下表包含发生错误时所特别感兴趣的那些值。  
  
|常量|“值”|Description|  
|--------------|-----------|-----------------|  
|**adFieldCantConvertValue**|2|指示的字段不能检索或存储而不会丢失数据。|  
|**adFieldDataOverflow**|6|指示从提供程序返回的数据溢出字段的数据类型。|  
|**adFieldDefault**|13|指示设置数据时，使用该字段的默认值。|  
|**adFieldIgnore**|15|指示在源中设置数据值时跳过此字段。 提供程序不设置任何值。|  
|**adFieldIntegrityViolation**|10|指示不能修改字段，因为它是计算或派生的实体。|  
|**adFieldIsNull**|3|指示提供程序返回一个 null 值。|  
|**adFieldOutOfSpace**|22|指示提供程序无法获取足够的存储空间来完成移动或复制操作。|