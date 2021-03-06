---
title: Analysis Services MDX 查询设计器（PowerPivot） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b1524b18-b9f1-46d2-a34e-dd7c91ca4684
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cd6b880fc1908d973b4a78fdc04cb59ed9eca731
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062471"
---
# <a name="analysis-services-mdx-query-designer-powerpivot"></a>Analysis Services MDX 查询设计器 (PowerPivot)
  Analysis Services 多维表达式（MDX）查询设计器提供了图形用户界面，可帮助您为[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]数据源创建 MDX 查询。 MDX 图形查询设计器有两种模式：设计模式和查询模式。 每种模式都提供一个“元数据”窗格，从该窗格中可以拖动所选多维数据集的成员，以生成可检索要使用的数据的 MDX 查询。  
  
> [!IMPORTANT]  
>  用户创建和运行查询时访问数据源。 您应授予对数据源的最小权限（如只读权限）。  
  
 以下几节介绍每种模式的图形查询设计器中的工具栏按钮和查询设计器窗格。  
  
## <a name="graphical-mdx-query-designer-in-design-mode"></a>设计模式下的图形 MDX 查询设计器  
 编辑 MDX 查询时，图形 MDX 查询设计器将以设计模式打开。  
  
 下图列出了设计模式的窗格。  
  
 ![Analysis Services MDX 查询设计器的设计视图](media/rsqd-dsawas-mdx-designmode.gif "Analysis Services MDX 查询设计器的设计视图")  
  
 下表列出了查询模式下的窗格：  
  
|窗格|函数|  
|----------|--------------|  
|选择“多维数据集”按钮 (**...**)|显示当前选定的多维数据集。|  
|“元数据”窗格|显示在选定多维数据集中定义的度量值、关键绩效指标 (KPI) 和维度的层次列表。|  
|“计算成员”窗格|显示当前定义的可在查询中使用的计算成员。|  
|“筛选器”窗格|用于选择维度和相关的层次结构，以筛选源中的数据并限制返回的数据。|  
|“数据”窗格|在从“元数据”窗格向“计算成员”窗格拖动项目时，显示结果集的列标题。 如果选中 **“自动执行”** 按钮，则可自动更新结果集。|  
  
 可以将“元数据”窗格中的维度、度量值和 KPI 以及“计算成员”窗格中的计算成员拖至“数据”窗格。 在“筛选器”窗格中，您可以选择维度和相关的层次结构，并设置筛选器表达式以限制可用于查询的数据。 如果工具栏上的“自动执行”****（![自动执行查询](media/rsqdicon-autoexecute.gif "自动执行查询")）切换按钮处于选中状态，那么每当你将元数据对象拖到“数据”窗格时，查询设计器都会运行查询。 可以使用工具栏上的“运行”****（![运行查询](media/rsqdicon-run.gif "运行查询")）按钮来手动运行查询。  
  
 在此模式下创建 MDX 查询时，下面的附加属性将会自动包含到查询中：  
  
 **成员属性** MEMBER_CAPTION, MEMBER_UNIQUE_NAME  
  
 **单元属性** VALUE、BACK_COLOR、FORE_COLOR、FORMATTED_VALUE、FORMAT_STRING、FONT_NAME、FONT_SIZE、FONT_FLAGS  
  
 若要指定您自己的附加属性，则必须在查询模式下，手动编辑 MDX 查询。  
  
 不支持从文件导入 .mdx 查询。  
  
> [!NOTE]  
>  有关 MDX 的详细信息以及有关 MDX 查询设计器的常规信息，请参阅 [SQL Server 联机丛书](https://go.microsoft.com/fwlink/?linkid=98335)中的“MDX 查询编辑器（Analysis Services - 多维数据）”。  
  
### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a>设计模式下的图形 MDX 查询设计器工具栏  
 查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。 下表列出了这些按钮及其功能。  
  
|Button|说明|  
|------------|-----------------|  
|**编辑为文本**|不可用于此数据源类型。|  
|**导入**|从文件系统中的报表定义 (.rdl) 文件导入现有查询。|  
|![更改为 MDX 查询视图](media/rsqdicon-commandtypemdx.gif "更改为 MDX 查询视图")|切换到命令类型 MDX。|  
|![刷新结果数据](media/rsqdicon-refresh.gif "刷新结果数据")|刷新数据源的元数据。|  
|![添加计算成员](media/rsqdicon-addcalculatedmember.gif "添加计算成员")|显示 **“计算成员生成器”** 对话框。|  
|![切换显示空单元](media/rsqdicon-showemptycells.gif "切换为显示空单元格")|在“数据”窗格中的显示或不显示空单元格之间切换。 （这等同于在 MDX 中使用 NON EMPTY 子句）。|  
|![自动执行查询](media/rsqdicon-autoexecute.gif "自动执行查询")|在每次进行更改时自动运行查询并显示结果。 结果将显示在“数据”窗格中。|  
|![“显示聚合”按钮](media/rsqdicon-showaggregations.gif "“显示聚合”按钮")|在“数据”窗格中显示聚合。|  
|![删除](media/rsqdicon-delete.gif "Delete")|通过查询在“数据”窗格中删除选定列。|  
|![“查询参数”对话框图标](media/iconqueryparameter.gif "“查询参数”对话框图标")|显示 **“查询参数”** 对话框。 指定查询参数的值时，会自动创建一个同名参数。|  
|![“准备查询”按钮](media/rsqdicon-preparequery.gif "“准备查询”按钮")|准备查询。|  
|![运行查询](media/rsqdicon-run.gif "运行查询")|运行查询并在“数据”窗格中显示结果。|  
|![取消查询](media/rsqdicon-cancel.gif "取消查询")|取消查询。|  
|![切换到设计模式](media/rsqdicon-designmode.gif "切换到设计模式")|在设计模式和查询模式之间切换。|  
  
## <a name="graphical-mdx-query-designer-in-query-mode"></a>查询模式下的图形 MDX 查询设计器  
 若要将图形查询设计器更改为 **“查询”** 模式，请单击工具栏上的 **“设计模式”** 按钮。  
  
 下图列出了查询模式的窗格。  
  
 ![Analysis Services MDX 查询设计器的查询视图](media/rsqd-dsawas-mdx-querymode.gif "Analysis Services MDX 查询设计器的查询视图")  
  
 下表列出了查询模式下的窗格：  
  
|窗格|函数|  
|----------|--------------|  
|选择“多维数据集”按钮 (**...**)|显示当前选定的多维数据集。|  
|元数据/函数/模板窗格|显示在选定多维数据集中定义的度量值、KPI 和维度的层次列表。|  
|“查询”窗格|显示查询文本。|  
|“结果”窗格|显示运行查询的结果。|  
  
 “元数据”窗格会显示 **“元数据”** 选项卡、 **“函数”** 选项卡和 **“模板”** 选项卡。 通过 **“元数据”** 选项卡，可将维度、层次结构、KPI 和度量值拖到“MDX 查询”窗格中。 通过 **“函数”** 选项卡，可将函数拖到“MDX 查询”窗格中。 通过 **“模板”** 选项卡，可将 MDX 模板添加到“MDX 查询”窗格中。 执行查询时，“结果”窗格将显示 MDX 查询的结果。  
  
 您可以扩展设计模式下生成的默认 MDX 查询，以包含附加成员属性和单元属性。 运行查询时，这些值不会显示在结果集中。 不过，这些值会随同数据集字段集合传递回来，并且您可以使用这些值。  
  
### <a name="graphical-query-designer-toolbar-in-query-mode"></a>查询模式下的图形查询设计器工具栏  
 查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。  
  
 工具栏按钮在设计模式和查询模式下是相同的，但是下列按钮在查询模式下不可用：  
  
-   **编辑为文本**  
  
-   **添加计算成员**（![添加计算成员](media/rsqdicon-addcalculatedmember.gif "添加计算成员")）  
  
-   **显示空单元格**（![切换为显示空单元格](media/rsqdicon-showemptycells.gif "切换为显示空单元格")）  
  
-   **自动执行**（![自动执行查询](media/rsqdicon-autoexecute.gif "自动执行查询")）  
  
-   **显示聚合**![“显示聚合”按钮](media/rsqdicon-showaggregations.gif "“显示聚合”按钮")  
  
  
