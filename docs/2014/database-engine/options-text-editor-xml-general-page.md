---
title: 选项（文本编辑器-XML-常规页） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 46a9f913-d0b9-40ff-b382-9bbdec7461a6
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b32dcfc95c5fc6929454add71ff4452e00fdda6e
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "83001039"
---
# <a name="options-text-editor---xml---general-page"></a>选项（“文本编辑器”-“XML”-“常规”页）
  使用此对话框可以更改 XML 编辑器（用于编辑 XML 文档）的常规编辑行为。 若要显示这些设置，请在 **“工具”** 菜单上单击 **“选项”** ，展开 **XML** 子文件夹，再单击 **“常规”**。  
  
## <a name="setting-options-in-multiple-locations"></a>在多个位置设置选项  
 XML 编辑器的选项也可在“所有语言”和“常规”对话框中设置。 **** 如果使用 "**所有语言**" 对话框来设置其他 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 编辑器（例如 DMX 或 MDX 编辑器）的其他选项，则必须使用此对话框重置 XML 编辑器选项。  
  
## <a name="statement-completion"></a>语句结束  
 **自动列出成员**  
 选中此复选框后，在编辑器中键入时会显示可用成员、属性、值或方法的列表。 从弹出列表中任选一项，即可将其插入到代码中。  
  
 **隐藏高级成员**  
 此复选框不可用。  
  
 **参数信息**  
 选中此复选框后，在编辑器中，当前声明或过程的完整语法会显示在插入点的左侧，并显示其所有可用参数。 下一个可分配参数以粗体显示。  
  
## <a name="settings"></a>设置  
 **启用虚拟空间**  
 如果选中此复选框，将在每个代码行末尾插入空格。 如果选中此复选框，可将注释始终定位在代码旁的同一位置。  
  
 **自动换行**  
 如果选中此复选框，则水平延伸到编辑器可见区域以外的行的其他部分都将自动显示在下一行。 选中此复选框将启用 **“显示可视的自动换行标志符号”** 复选框。  
  
 **显示可视的自动换行标志符号**  
 如果选中此复选框，则在长行换行的位置显示返回箭头指示符。 如果不希望显示这些指示符，请清除此复选框。  
  
> [!NOTE]  
>  这些提示箭头不会添加到代码中，也不会打印出来。 它们仅供参考。  
  
 **没有选定内容时对空行应用剪切或复制命令**  
 此复选框用于设置将插入点放在空白行上，不选择任何内容，再单击 **“复制”** 或 **“剪切”** 时的编辑器行为。  
  
 如果选中此复选框，将复制或剪切空白行。 如果随后单击 **“粘贴”**，将插入一个新空白行。  
  
 如果此复选框处于未选中状态，则不复制或剪切任何内容。 如果随后单击 **“粘贴”**，将粘贴最近一次复制的内容。 如果以前尚未复制任何内容，则不会粘贴任何内容。  
  
 如果不是空白行，则此设置对 **“复制”** 或 **“剪切”** 无效。 如果没有选定任何内容，将复制或剪切整个行。 如果随后单击 **“粘贴”**，将粘贴整个行的文本及其行终止符。  
  
## <a name="display"></a>显示  
 **行号**  
 如果选中此复选框，则将在每个代码行的旁边显示行号。  
  
> [!NOTE]  
>  这些行号不会添加到代码中，也不会打印出来。 它们仅供参考。  
  
 **启用单击 URL 定位**  
 选中此复选框后，当光标在编辑器中的 URL 上方经过时，光标会变为手形指针。 您可以单击 URL 以在 Web 浏览器中显示所指示的页。  
  
 **导航栏**  
 此复选框不可用。  
  
  
