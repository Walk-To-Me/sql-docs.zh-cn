---
title: PATH 模式中的命名空间支持 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 39fd399838ac2e94672f3f416a2c83e4233060d3
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702582"
---
# <a name="namespace-support-in-path-mode"></a>PATH 模式中的命名空间支持
  PATH 模式中的命名空间支持是通过使用 WITH NAMESPACES 提供的。 例如，下面的查询演示了如何使用 WITH NAMESPACES 语法声明一个命名空间 (a:)，随后即可在后续的 SELECT 语句中使用此命名空间：  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>示例  
 以下这些示例演示了使用 PATH 模式从 SELECT 查询生成 XML 的过程。 这些查询中有许多都是针对 ProductModel 表的 Instructions 列中存储的自行车生产说明 XML 文档指定的。  
  
## <a name="see-also"></a>另请参阅  
 [将 PATH 模式与 FOR XML 一起使用](use-path-mode-with-for-xml.md)  
  
  
