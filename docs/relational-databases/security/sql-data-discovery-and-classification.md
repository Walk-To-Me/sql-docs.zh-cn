---
title: SQL 数据发现和分类 | Microsoft Docs
description: SQL 数据发现和分类
documentationcenter: ''
ms.reviewer: vanto
ms.assetid: 89c2a155-c2fb-4b67-bc19-9b4e03c6d3bc
ms.service: sql-database
ms.prod_service: sql-database,sql
ms.custom: security
ms.topic: conceptual
ms.date: 09/12/2019
ms.author: mibar
author: barmichal
ms.openlocfilehash: 077a9a6be533ec05f9c062100d04bf02562f6066
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2020
ms.locfileid: "75548336"
---
# <a name="sql-data-discovery-and-classification"></a>SQL 数据发现和分类
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

数据发现和分类引入了全新工具，并将其内置于 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)，以便发现数据库中的敏感数据并对其进行分类、标记和报告   。
发现最敏感的数据（如商业、金融、医疗等）并对其进行分类在组织的信息保护中可起到关键作用。 它可以充当基础结构，用于：
* 帮助满足数据隐私标准。
* 控制对包含高度敏感数据的数据库/列的访问，并加强其安全性。

> [!NOTE]
> SQL Server 2012 及更高版本支持数据发现和分类，这些功能可用于 [SSMS 17.5](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 或更高版本。 有关 Azure SQL 数据库，请参阅 [Azure SQL 数据库数据发现和分类](/azure/sql-database/sql-database-data-discovery-and-classification/)。

## <a name="overview"></a><a id="subheading-1"></a>概述
数据发现和分类引入了一套高级服务，形成了一种旨在保护各种数据（而不只是数据库）的全新 SQL 信息保护范例：

* 发现和建议 - 分类引擎扫描数据库，并标识包含潜在敏感数据的列。 利用它可以轻松查看和应用相应的分类建议，也可以手动对列进行分类。
* 标记 - 可以在列上永久地标记敏感度分类标签。
* 可见性 - 可以在详细报表中查看数据库分类状态，如在符合性和审核等事项中对其有需求，则可以直接打印/导出该报表。

## <a name="discovering-classifying--labeling-sensitive-columns"></a><a id="subheading-2"></a>发现、分类和标记敏感列
以下部分介绍如何在数据库中发现包含敏感数据的列并对其进行分类和标记、如何查看数据库的当前分类状态，以及如何导出报表。

分类包含两种元数据属性：
* 标签 - 这是主要的分类属性，用于定义存储在列中的数据的敏感度级别。  
* 信息类型 - 为列中存储的数据类型提供额外的粒度。

**对 SQL Server 数据库进行分类：**

1. 在 SQL Server Management Studio (SSMS) 中连接到 SQL Server。

2. 在 SSMS 对象资源管理器中，右键单击要分类的数据库，并选择“任务” > “数据发现和分类” > “对数据进行分类...”  。

   ![“导航”窗格][0]

3. 分类引擎扫描数据库，寻找包含潜在敏感数据的列，并提供“建议的列分类”列表：

    * 要查看建议的列分类列表，请单击窗口顶部的建议通知框，或底部的建议面板：

        ![“导航”窗格][2]

        ![“导航”窗格][3]

    * 查看建议列表：
        * 要接受针对某特定列的建议，请选中相关行左侧列中的复选框。 还可以选中建议表标头中的复选框，将所有建议标记为“接受”。

        * 也可以使用下拉框更改建议的信息类型和敏感度标签。        

        ![“导航”窗格][4]

    * 要应用所选建议，请单击蓝色的“接受所选建议”按钮。

        ![“导航”窗格][5]

4. 此外，还可以手动对列进行分类，或基于建议分类：

    * 单击窗口顶部菜单中的“添加分类”。

        ![“导航”窗格][6]

    * 在打开的上下文窗口中，选择要分类的“架构”>“表”>“列”，并选择信息类型和敏感度标签。 然后单击上下文窗口底部的蓝色“添加分类”按钮。

        ![“导航”窗格][7]

5. 要完成分类，并永久地使用新分类元数据标记数据库列，请在窗口顶部菜单中单击“保存”。

    ![“导航”窗格][8]


6. 要生成数据库分类状态的完整摘要报表，请在窗口顶部菜单中单击“查看报表”。 （也可以使用 SSMS 生成报告。 右键单击要生成报告的数据库，然后选择“任务” > “数据发现和分类” > “生成报告...”  ）

    ![“导航”窗格][9]

    ![“导航”窗格][10]

## <a name="manage-information-protection-policy-with-ssms"></a><a id="subheading-3"></a>使用 SSMS 管理信息保护策略

你可以使用 [SSMS 18.4](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 或更高版本来管理信息保护策略：

1. 在 SQL Server Management Studio (SSMS) 中连接到 SQL Server。

2. 在 SSMS 对象资源管理器中，右键单击一个数据库，然后选择“任务” > “数据发现和分类” 。

   你可以使用以下菜单选项来管理信息保护策略：

* **设置信息保护策略文件**：使用所选 JSON 文件中定义的信息保护策略。

* **导出信息保护策略**：将信息保护策略导出到 JSON 文件。

* **重置信息保护策略**：将信息保护策略重置为默认信息保护策略。

> [!IMPORTANT]
> 信息保护策略文件不存储在 SQL Server 中。
> SSMS 使用默认的信息保护策略。 如果自定义的信息保护策略失败，SSMS 将无法使用默认策略。 数据分类失败。 要解决此问题，请单击“重置信息保护策略”以使用默认策略并重新启用数据分类。

## <a name="accessing-the-classification-metadata"></a><a id="subheading-4"></a>访问分类元数据

SQL Server 2019 引入了 [`sys.sensitivity_classifications`](../system-catalog-views/sys-sensitivity-classifications-transact-sql.md) 系统目录视图。 此视图返回信息类型和敏感度标签。 

> [!NOTE]
> 此视图需要 VIEW ANY SENSITIVITY CLASSIFICATION 权限。 有关详细信息，请参阅 [Metadata Visibility Configuration](https://docs.microsoft.com/sql/relational-databases/security/metadata-visibility-configuration?view=sql-server-ver15)。

在 SQL Server 2019 实例上，查询 `sys.sensitivity_classifications` 以查看所有具有相应分类的已分类列。 例如： 

```sql
SELECT 
    schema_name(O.schema_id) AS schema_name,
    O.NAME AS table_name,
    C.NAME AS column_name,
    information_type,
    label
FROM sys.sensitivity_classifications sc
    JOIN sys.objects O
    ON  sc.major_id = O.object_id
    JOIN sys.columns C 
    ON  sc.major_id = C.object_id  AND sc.minor_id = C.column_id
```

在低于 SQL Server 2019 的实例上，信息类型和敏感度标签的分类元数据位于以下扩展属性中： 

* `sys_information_type_name`
* `sys_sensitivity_label_name`

可以使用扩展属性目录视图 [`sys.extended_properties`](../system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md) 访问元数据。

对于 SQL Server 2017 及之前的实例，以下示例返回具有相应分类的所有已分类列：

```sql
SELECT
    schema_name(O.schema_id) AS schema_name,
    O.NAME AS table_name,
    C.NAME AS column_name,
    information_type,
    sensitivity_label 
FROM
    (
        SELECT
            IT.major_id,
            IT.minor_id,
            IT.information_type,
            L.sensitivity_label 
        FROM
        (
            SELECT
                major_id,
                minor_id,
                value AS information_type 
            FROM sys.extended_properties 
            WHERE NAME = 'sys_information_type_name'
        ) IT 
        FULL OUTER JOIN
        (
            SELECT
                major_id,
                minor_id,
                value AS sensitivity_label 
            FROM sys.extended_properties 
            WHERE NAME = 'sys_sensitivity_label_name'
        ) L 
        ON IT.major_id = L.major_id AND IT.minor_id = L.minor_id
    ) EP
    JOIN sys.objects O
    ON  EP.major_id = O.object_id 
    JOIN sys.columns C 
    ON  EP.major_id = C.object_id AND EP.minor_id = C.column_id
```

## <a name="manage-classifications"></a><a id="subheading-5"></a>管理分类

# <a name="t-sql"></a>[T-SQL](#tab/t-sql)
可以使用 T-SQL 添加/删除列分类，以及检索整个数据库的所有分类。

- 添加/更新一列或多列分类：[添加敏感度分类](https://docs.microsoft.com/sql/t-sql/statements/add-sensitivity-classification-transact-sql)
- 删除一列或多列分类：[删除敏感度分类](https://docs.microsoft.com/sql/t-sql/statements/drop-sensitivity-classification-transact-sql)

# <a name="powershell-cmdlet"></a>[PowerShell Cmdlet](#tab/sql-powelshell)
可以使用 PowerShell Cmdlet 添加/删除列分类，以及检索整个数据库的所有分类并获取建议。

- [Get-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlSensitivityClassification?view=sqlserver-ps)
- [Get-SqlSensitivityRecommendations](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlSensitivityRecommendations?view=sqlserver-ps)
- [Set-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Set-SqlSensitivityClassification?view=sqlserver-ps)
- [Remove-SqlSensitivityClassification](https://docs.microsoft.com/powershell/module/sqlserver/Remove-SqlSensitivityClassification?view=sqlserver-ps)

---

## <a name="next-steps"></a><a id="subheading-6"></a>后续步骤

有关 Azure SQL 数据库，请参阅 [Azure SQL 数据库数据发现和分类](https://go.microsoft.com/fwlink/?linkid=866265)。

请考虑通过应用列级别安全性机制来保护敏感列：

* 用于模糊化使用中的敏感列的[动态数据掩码](https://docs.microsoft.com/sql/relational-databases/security/dynamic-data-masking)。
* 用于静态加密敏感列的 [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)。

<!--Anchors-->
[SQL Data Discovery & Classification overview]: #subheading-1
[Discovering, classifying & labeling sensitive columns]: #subheading-2
[Manage information protection policy with SSMS]: #subheading-3
[Accessing the classification metadata]: #subheading-4
[Manage classifications]: #subheading-5
[Next Steps]: #subheading-6

<!--Image references-->

[0]: ./media/sql-data-discovery-and-classification/0-data-classification-explorer.png
[2]: ./media/sql-data-discovery-and-classification/2-recommendations-notification-box.png
[3]: ./media/sql-data-discovery-and-classification/3-recommendations-panel.png
[4]: ./media/sql-data-discovery-and-classification/4-recommendations.png
[5]: ./media/sql-data-discovery-and-classification/5-accept-recommendations-button.png
[6]: ./media/sql-data-discovery-and-classification/6-add-classification-button.png
[7]: ./media/sql-data-discovery-and-classification/7-manual-classification.png
[8]: ./media/sql-data-discovery-and-classification/8-save.png
[9]: ./media/sql-data-discovery-and-classification/9-view-report.png
[10]: ./media/sql-data-discovery-and-classification/10-report.png
