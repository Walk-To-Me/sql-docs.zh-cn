---
title: 查看多维数据集架构 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 82fc715c-e08e-447d-8fc8-9c9005f145f0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b094e27a8b7c51afec21fcc4807d3ee6e8b22c37
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072504"
---
# <a name="view-the-cube-schema"></a>查看多维数据集架构
  在 **“多维数据集设计器”** 的 **“多维数据集结构”** 选项卡的 **“数据源视图”** 窗格中显示多维数据集架构。 架构是从中派生多维数据集的度量值和维度的表的集合。 每个多维数据集架构包含多维数据集中的度量值和维度基于的一个或多个事实表以及一个或多个维度表。  
  
 **“多维数据集结构”** 选项卡的 **“数据源视图”** 窗格显示多维数据集所基于的数据源视图的关系图。 此关系图是数据源视图主关系图的一个子集。 您可以在 **“数据源视图”** 窗格中隐藏和显示表并查看任何现有的关系图。 但是，您不能更改（例如添加新关系或命名查询）基础架构。 若要更改该架构，请使用数据源视图设计器。  
  
 创建多维数据集时， **“多维数据集结构”** 选项卡的 **“数据源视图”** 窗格中显示的关系图最初与项目或数据库的数据源视图中的 **“显示所有表”** 关系图相同。 您可以在 **“数据源视图”** 窗格中使用数据源视图中任何现有的关系图替换此关系图并进行调整。  
  
 在 **“多维数据集设计器”** 中使用关系图时，作用于选项卡或选项卡中任何所选对象的命令都会在 **“数据源视图”** 菜单中提供。 您还可以右键单击关系图的背景或关系图中的任何对象来使用作用于关系图或所选对象的命令。 你可以：  
  
-   在关系图和树视图之间进行切换。  
  
-   排列、查找、显示和隐藏表。  
  
-   显示友好名称。  
  
-   切换布局。  
  
-   更改放大倍数。  
  
-   查看属性。  
  
 此外，您可以执行下表中所列的操作：  
  
|功能|操作|  
|--------|-------------|  
|从多维数据集的数据源视图使用关系图|在 **“数据源视图”** 菜单上，指向 **“关系图复制源”**，然后单击要使用的数据源视图关系图。<br /><br /> - 或 -<br /><br /> 右键单击“数据源视图”窗格的背景，指向“关系图复制源”********，然后单击要使用的数据源视图中的关系图。 此方法创建关系图的一个独立副本，因此您在 **“多维数据集生成器”** 选项卡上的任何更改不会显示在原始关系图中。|  
|只显示多维数据集中使用的表|在 **“数据源视图”** 菜单上，单击 **“仅显示已用表”**。<br /><br /> - 或 -<br /><br /> 右键单击“数据源视图”窗格的背景，然后单击“仅显示已用表”********。|  
|编辑数据源视图架构|在 **“数据源视图”** 菜单上，单击 **“编辑数据源视图”**。<br /><br /> - 或 -<br /><br /> 右键单击“数据源视图”窗格的背景，然后单击“编辑数据源视图”********。|  
  
  
