---
title: 为 OLE DB 表值参数更改的架构行集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4b51f1d6b3e8a7a75574e78e24e27b5d9d75df42
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704612"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>为 OLE DB 表值参数更改的架构行集
  以下为已更改或添加以支持表值参数的架构行集。  
  
|架构行集|说明|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|在名为 SS_TYPE_CATALOG_NAME 和 SS_TYPE_SCHEMANAME 的行集末尾添加了两个新列。 这些列可供将来的类型重用。 TYPE_NAME 和 LOCAL_TYPE_NAME 列将包含表值参数 TABLE 类型的名称。 DATA_TYPE 列将具有表值参数的值 DBTYPE_TABLE = 143。|  
|DBSCHEMA_TABLE_TYPES|添加了此行集以支持表值参数。 此行集与 DBSCHEMA_TABLES 基本相同，不同的是它仅为表类型而非表、视图或同义词返回元数据。 TABLE_TYPE 列将具有值“TABLE TYPE”。|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|添加了此行集以支持表值参数。 此行集与 DBSCHEMA_PRIMARY_KEYS 基本相同，不同的是它只为表类型而非表返回主键元数据。|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|添加了此行集以支持表值参数。 此行集与 DBSCHEMA_COLUMNS 基本相同，不同的是它仅为表类型而非表、视图或同义词返回列元数据。|  
  
## <a name="see-also"></a>另请参阅  
 [表值参数 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [使用表值参数 (OLE DB)](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
