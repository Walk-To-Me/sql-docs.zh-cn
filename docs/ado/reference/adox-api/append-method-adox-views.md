---
title: Append 方法（ADOX 视图） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
author: rothja
ms.author: jroth
ms.openlocfilehash: 540ff52141139f4748cb2cd4c8979f5f8b55b230
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763998"
---
# <a name="append-method-adox-views"></a>Append 方法（ADOX 视图）
创建新的[视图](../../../ado/reference/adox-api/view-object-adox.md)对象并将其追加到[Views](../../../ado/reference/adox-api/views-collection-adox.md)集合。  
  
## <a name="syntax"></a>语法  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>参数  
 *Name*  
 一个**字符串**值，该值指定要创建的视图的名称。  
  
 *命令*  
 一个 ADO[命令](../../../ado/reference/ado-api/command-object-ado.md)对象，表示要创建的视图。  
  
## <a name="remarks"></a>备注  
 使用**Command**对象中指定的名称和属性在数据源中创建新视图。  
  
 如果用户指定的命令文本表示过程而不是视图，则行为取决于提供程序。 如果提供程序不支持保留命令，则**Append**将会失败。  
  
> [!NOTE]
>  使用 Microsoft Jet 的 OLE DB 提供程序时， **Views**集合**Append**方法将允许您在*Command*参数中指定**过程**，而不是**视图**。 该**过程**将添加到数据源，并将添加到**Views**集合。 **追加**后，如果刷新了**过程**和**视图**集合，则该**过程**将不再出现在**Views**集合中并且会出现在 "**过程**" 集合中。  
  
## <a name="applies-to"></a>应用于  
 [视图集合 (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>另请参阅  
 [Views Append 方法示例（VB）](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Append 方法（ADOX 列）](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append 方法（ADOX 组）](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append 方法（ADOX 索引）](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append 方法（ADOX 键）](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append 方法（ADOX 过程）](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append 方法（ADOX 表）](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append 方法（ADOX 用户）](../../../ado/reference/adox-api/append-method-adox-users.md)
