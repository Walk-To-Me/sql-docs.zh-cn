---
title: 使用 targetNamespace 属性指定目标命名空间（SQLXML 4.0） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2f8b16b07919c1157abe417fa0e92aff4f198f48
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703520"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a>使用 targetNamespace 属性指定目标命名空间 (SQLXML 4.0)
  在编写 XSD 架构时，可以使用 XSD **targetNamespace**属性指定目标命名空间。 本主题介绍 XSD **targetNamespace**、 **elementFormDefault**和**attributeFormDefault**属性如何工作，如何影响生成的 XML 实例，以及如何使用命名空间指定 XPath 查询。  
  
 您可以使用**xsd： targetNamespace**属性将默认命名空间中的元素和属性放入不同的命名空间中。 还可以指定在显示局部声明的架构元素和属性时，是否应由命名空间限定（使用前缀显式限定或默认隐式限定）。 您可以使用** \< xsd： schema>** 元素上的**elementFormDefault**和**attributeFormDefault**属性来全局指定本地元素和属性的限定，或者可以使用**窗体**属性单独指定单独的元素和属性。  
  
## <a name="examples"></a>示例  
 若要创建使用以下示例的工作示例，必须满足某些要求。 有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。  
  
### <a name="a-specifying-a-target-namespace"></a>A. 指定目标命名空间  
 以下 XSD 架构使用**XSD： targetNamespace**属性指定目标命名空间。 该架构还会将**elementFormDefault**和**attributeFormDefault**属性值设置为 **"未限定"** （这些属性的默认值）。 这是一种全局声明，它会影响架构中的所有本地元素（** \< 顺序>** ）和属性（**CustomerID**、"**联系人姓名**" 和 "**订单 id** "）。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 在架构中：  
  
-   **CustomerType**和**OrderType**类型声明是全局的，因此包含在架构的目标命名空间中。 因此，当在** \< Customer>** 元素的声明中引用这些类型，并将其** \< 顺序>** 子元素时，将指定与目标命名空间关联的前缀。  
  
-   ** \< Customer>** 元素也包含在架构的目标命名空间中，因为它是架构中的全局元素。  
  
 针对该架构执行以下 XPath 查询：  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 该 XPath 查询生成以下实例文档（仅显示了一部分订单）：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 此实例文档定义了 urn： MyNamespace 命名空间，并将前缀（y0）与该命名空间相关联。 前缀仅适用于** \< Customer>** 全局元素。 （元素是全局性的，因为它被声明为架构中的** \< xsd： schema>** 元素的子元素。）  
  
 前缀不适用于本地元素和属性，因为**elementFormDefault**和**attributeFormDefault**属性的值在架构中设置为 **"非限定"** 。 请注意， ** \< Order>** 元素是局部的，因为其声明显示为** \< complexType>** 元素的子元素，该元素定义** \< CustomerType>** 元素。 同样，属性（**CustomerID**、**订单 Id**和**联系人姓名**）是本地的，而不是全局的。  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>创建此架构的工作示例  
  
1.  复制上面的架构代码，并将它粘贴到文本文件中。 将文件另存为 targetNameSpace.xml。  
  
2.  复制以下模板，并将它粘贴到文本文件中。 在保存 targetNamespace.xml 的目录中将该文件另存为 targetNameSpaceT.xml。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     模板中的 XPath 查询将返回 CustomerID 为1的客户的** \< customer>** 元素。 请注意，XPath 查询为查询中的元素（而不是属性）指定命名空间前缀。 （根据架构中的指定，未限定局部属性。）  
  
     为映射架构 (targetNamespace.xml) 指定的目录路径是相对于模板保存目录的相对路径。 也可以指定绝对路径，例如：  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。  
  
     有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。  
  
 如果架构指定了值为 **"限定"** 的**elementFormDefault**和**attributeFormDefault**属性，实例文档将具有限定的所有局部元素和属性。 您可以更改以前的架构，以便在** \< xsd： schema>** 元素中包含这些属性，并再次执行模板。 由于当前在实例中也限定了这些属性，XPath 查询将改为包括命名空间前缀。  
  
 下面是修改后的 XPath 查询：  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 下面是返回的 XML 文档：  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  
