---
title: 数据函数（XQuery） |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:data function
- data function [XQuery]
ms.assetid: 511b5d7d-c679-4cb2-a3dd-170cc126f49d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7376c57f809fa97168b27b158678d931a696b5df
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038969"
---
# <a name="data-accessor-functions---data-xquery"></a>数据取值函数 - data (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  返回 *$arg*指定的每个项的类型化值。  
  
## <a name="syntax"></a>语法  
  
```  
  
fn:data ($arg as item()*) as xdt:untypedAtomic*  
```  
  
## <a name="arguments"></a>参数  
 *$arg*  
 将返回其类型化值的各项的顺序。  
  
## <a name="remarks"></a>备注  
 下列情况适用于类型化值：  
  
-   原子值的类型化值是原子值。  
  
-   文本节点的类型化值是文本节点的字符串值。  
  
-   注释的类型化值是注释的字符串值。  
  
-   处理指令的类型化值是处理指令的内容，不含处理指令目标名称。  
  
-   文档节点的类型化值是文档节点的字符串值。  
  
 下列情况适用于属性节点和元素节点：  
  
-   如果属性节点用 XML 架构类型类型化，则相应地，该节点的类型化值就是类型化值。  
  
-   如果特性节点是非类型化的，则其类型化值等于其作为**xdt： untypedAtomic**的实例返回的字符串值。  
  
-   如果未键入元素节点，则其类型化值等于其作为**xdt： untypedAtomic**的实例返回的字符串值。  
  
 下列情况适用于类型化元素节点：  
  
-   如果元素具有简单内容类型，则**data （）** 将返回元素的类型化值。  
  
-   如果节点是复杂类型（包括 xs： anyType），则**data （）** 将返回一个静态错误。  
  
 尽管使用**data （）** 函数通常是可选的（如下面的示例中所示），但指定**data （）** 函数会明确提高查询的可读性。 有关详细信息，请参阅[XQuery 基础知识](../xquery/xquery-basics.md)。  
  
 不能在构造的 XML 上指定**data （）** ，如下所示：  
  
```  
declare @x xml  
set @x = ''  
select @x.query('data(<SomeNode>value</SomeNode>)')  
```  
  
## <a name="examples"></a>示例  
 本主题提供了针对 AdventureWorks 数据库中各种**xml**类型列中存储的 xml 实例的 XQuery 示例。  
  
### <a name="a-using-the-data-xquery-function-to-extract-typed-value-of-a-node"></a>A. 使用 data() XQuery 函数提取节点的类型化值  
 下面的查询演示了如何使用**data （）** 函数来检索属性、元素和文本节点的值：  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query(N'  
 for $pd in //p1:ProductDescription  
 return   
    <Root   
      ProductID = "{ data( ($pd//@ProductModelID)[1] ) }"   
      Feature =   "{ data( ($pd/p1:Features/wm:Warranty/wm:Description)[1] ) }" >  
    </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 结果如下：  
  
```  
<Root ProductID="19" Feature="parts and labor"/>  
```  
  
 如前所述，在构造属性时， **data （）** 函数是可选的。 如果未指定**data （）** 函数，则会隐式假定该函数。 下面的查询将与前面的查询生成相同的结果：  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
      for $pd in //p1:ProductDescription  
         return   
          <Root    
                ProductID = "{ ($pd/@ProductModelID)[1] }"    
                Feature =   "{ ($pd/p1:Features/wm:Warranty/wm:Description)[1] }" >  
           </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 下面的示例说明了需要**data （）** 函数的实例。  
  
 在下面的查询中， **$pd/p1：规范/材料**返回 <`Material`> 元素。 此外， **data （$pd/p1：规范/材料）** 返回类型为 Xdt： untypedAtomic 的字符数据，因为`Material` <> 是非类型化的。 如果输入是非类型化的，则**data （）** 的结果类型为**xdt： untypedAtomic**。  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      for $pd in //p1:ProductDescription  
         return   
          <Root>  
             { $pd/p1:Specifications/Material }  
             { data($pd/p1:Specifications/Material) }  
           </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 结果如下：  
  
```  
<Root>  
  <Material>Almuminum Alloy</Material>Almuminum Alloy  
</Root>  
```  
  
 在下面的查询中， **data （$pd/p1： Features/wm：保修期）** 将返回一个静态错误， `Warranty`因为 <> 是一个复杂类型元素。  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
 <Root>  
   {     /p1:ProductDescription/p1:Features/wm:Warranty }  
   { data(/p1:ProductDescription/p1:Features/wm:Warranty) }  
 </Root>  
 ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID = 23  
```  
  
## <a name="see-also"></a>另请参阅  
 [针对 xml 数据类型的 XQuery 函数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
