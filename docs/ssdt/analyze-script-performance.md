---
title: 分析脚本性能 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.codeanalysis.configuring
ms.assetid: f4bbdd31-12a5-4c57-b0fe-1c6683820f11
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ba3c41e2366643e07f07307537e735ec8d259d0e
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086029"
---
# <a name="analyze-script-performance"></a>分析脚本性能
可以使用 SQL Server Data Tools 提供的工具确定是否可以提高你的查询、存储过程或脚本的性能。 例如，通过监视常用查询的响应时间之类的客户端统计信息，可以确定是否需要更改表的查询或索引。 此类统计信息可包括客户端执行时间、查询配置文件、已发送和接收的数据包/字节。  
  
此外，也可以通过以下方法更好地解决某些性能问题：分析应用程序提交给数据库的应用程序查询和更新，并分析这些查询和更新如何与数据库中包含的数据及数据库架构进行交互。 执行计划以图形方式显示 SQL Server 查询优化器选择的数据检索方法，并且显示特定语句和查询的执行系统开销。 因此，它们可以帮助了解 SQL Server 将如何处理你的 SQL 查询，并确定导致性能下降的因素。  
  
## <a name="using-client-statistics"></a>使用客户端统计信息  
当在 Transact\-SQL 编辑器中运行脚本或查询时，可以选择收集客户端统计信息，例如应用程序配置文件、网络和用于执行的时间统计信息。 通过此类度量，您可以衡量您的脚本的效率或评测不同的脚本。  
  
若要切换客户端统计信息的收集，请在 Transact\-SQL 编辑器打开时，在“数据”菜单上，指向“Transact\-SQL 编辑器”，然后单击“执行设置”和“包括客户端统计信息”。 或者，单击 Transact\-SQL 编辑器工具栏上的“包括客户端统计信息”按钮（从右边数第五个按钮），或在 Transact\-SQL 编辑器中右键单击，然后选择“执行设置”和“包括客户端统计信息”。 请注意，为了收集查询的统计信息，您必须在执行前启用此功能。  
  
如果启用了客户端统计信息，则“统计信息”选项卡将在查询执行时出现在“消息”选项卡的旁边。 如果禁用客户端统计信息，则不会出现“统计信息”选项卡。 连续查询执行中的统计信息会与平均值一起列出。  
  
有关收集的统计信息的详细信息，请参阅[“查询窗口统计信息”窗格](http://msdn.microsoft.com/en-us/library/aa216969(SQL.80).aspx)和[此主题的“‘客户端统计信息’选项卡”一节](http://msdn.microsoft.com/en-us/library/aa833205.aspx)。  
  
## <a name="using-execution-plans"></a>使用执行计划  
执行计划显示数据库引擎是如何通过导航表和使用索引来访问或处理查询的数据或其他 DML 语句（例如 update）的。 这种图形表示法对了解查询的性能特征非常有用。  
  
打开包含要在 Transact\-SQL 编辑器中进行分析的查询的 Transact\-SQL 脚本。 然后，可以突出显示要查看的代码，并通过单击编辑器工具栏上的“显示估计的执行计划”按钮，选择显示估计的执行计划。 如果单击“显示估计的执行计划”，则 Transact\-SQL 查询或批处理将不会运行。 而是会对脚本进行分析，并且会显示在实际执行查询时数据库引擎将极有可能使用的查询执行计划。  
  
分析或执行脚本之后，请单击“执行计划”选项卡以查看执行计划输出的图形表示方式。  
  
按照从右到左、从上到下的方式读取图形执行计划输出。 将显示所分析的批处理中的每个查询，包括每个查询的开销占批处理总开销的百分比。 若要查看其他信息（例如每个步骤的系统开销和操作），请将鼠标指针悬停在图形计划中的[逻辑和物理运算符图标](http://msdn.microsoft.com/en-us/library/ms175913.aspx)上。  
  
若要更改执行计划的显示，请右键单击“执行计划”并选择“放大”、“缩小”、“自定义显示比例”或“缩放到合适大小”。 “放大”和“缩小”允许你按固定量扩大或减小执行计划。 “自定义缩放” 允许你定义自己的显示放大倍数，例如缩放到 80%。  “缩放到合适大小”调整执行计划以适应结果窗格。  
  
执行计划可以保存并且在以后重新打开以便进行检查。 为此，请右键单击“执行计划”，然后选择“将执行计划另存为”。 之后，可以在 Visual Studio 中打开该计划，就像打开任何其他类型的文件一样。  
  
## <a name="using-code-analysis"></a>使用代码分析  
可以使用代码分析发现您的脚本中的潜在问题，例如设计、命名和性能问题。  数据库项目的规则组织成针对特定领域的预定义的规则集，并且您可以在 **“项目属性”** 属性页的 **“代码分析”** 选项卡中启用或禁用任何规则。 在同一个选项卡上，您可以指定代码分析以便在每次生成项目时自动运行，或者指定是否将警告视为错误。  
  
若要手动使用代码分析，请在“解决方案资源管理器”中右键单击你的项目，然后选择“运行代码分析”。 代码分析警告在 **“错误列表”** 窗口中列出。 可以双击某一警告以便导航到包含该问题的源代码，并且可以通过使用“显示错误帮助”上下文菜单查看警告的附加信息和可能的更正措施。  
  
有关代码分析的详细信息，请参阅 [分析数据库代码以提高代码质量](http://msdn.microsoft.com/en-us/library/dd172133.aspx)。  
  