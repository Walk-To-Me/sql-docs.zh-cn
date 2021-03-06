---
title: 大容量复制函数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 41677f84b3d689cee12d1bdbf38a8bcdc0b7c995
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705262"
---
# <a name="bulk-copy-functions"></a>大容量复制函数
  使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序的特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的大容量复制 API 扩展，客户端应用程序可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中快速添加或提取数据行。  
  
 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 时，您可以在 SQLNCLI11.LIB 和 SQLNCLI.H 中引用大容量复制函数 (BCP)。  
  
 使用 BCP API 函数调用的应用程序应与随该应用程序使用的驱动程序 (.dll) 提供的库 (.lib) 建立链接。 BCP 应用程序不应链接到多个驱动程序库。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [bcp_batch](bcp-batch.md)  
  
-   [bcp_bind](bcp-bind.md)  
  
-   [bcp_colfmt](bcp-colfmt.md)  
  
-   [bcp_collen](bcp-collen.md)  
  
-   [bcp_colptr](bcp-colptr.md)  
  
-   [bcp_columns](bcp-columns.md)  
  
-   [bcp_control](bcp-control.md)  
  
-   [bcp_done](bcp-done.md)  
  
-   [bcp_exec](bcp-exec.md)  
  
-   [bcp_getcolfmt](bcp-getcolfmt.md)  
  
-   [bcp_gettypename](bcp-gettypename.md)  
  
-   [bcp_init](bcp-init.md)  
  
-   [bcp_moretext](bcp-moretext.md)  
  
-   [bcp_readfmt](bcp-readfmt.md)  
  
-   [bcp_sendrow](bcp-sendrow.md)  
  
-   [bcp_setbulkmode](bcp-setbulkmode.md)  
  
-   [bcp_setcolfmt](bcp-setcolfmt.md)  
  
-   [bcp_writefmt](bcp-writefmt.md)  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server 驱动程序扩展](../../database-engine/dev-guide/sql-server-driver-extensions.md)   
 [&#40;ODBC&#41;执行大容量复制操作](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
