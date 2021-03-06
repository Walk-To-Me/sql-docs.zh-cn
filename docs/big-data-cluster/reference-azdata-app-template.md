---
title: azdata app template 参考
description: azdata app template 命令的参考文章。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: da1b98649eeb48d5ae2d6ca05e61da53f519e944
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "75251057"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

以下文章提供了 `azdata` 工具中 `app template` 命令的参考。 有关其他 `azdata` 命令的详细信息，请参阅 [azdata 参考](reference-azdata.md)

## <a name="commands"></a>命令
|     |     |
| --- | --- |
[`azdata app template list`](#azdata-app-template-list) | 提取支持的模板。
[`azdata app template pull`](#azdata-app-template-pull) | 下载支持的模板。
## <a name="azdata-app-template-list"></a>azdata app template list
提取指定的 [URL] github 存储库下支持的模板。
```bash
azdata app template list [--url -u]
```
### <a name="examples"></a>示例
提取默认模板存储库位置下的所有模板。
```bash
azdata app template list
```
提取不同存储库位置下的所有模板。
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>可选参数
#### `--url -u`
指定其他模板存储库位置。 默认： https://github.com/Microsoft/SQLBDC-AppDeploy.git
### <a name="global-arguments"></a>全局参数
#### `--debug`
提高日志记录详细程度以显示所有调试日志。
#### `--help -h`
显示此帮助消息并退出。
#### `--output -o`
输出格式。  允许的值：json、jsonc、table、tsv。  默认值：json。
#### `--query -q`
JMESPath 查询字符串。 请参阅 [http://jmespath.org/](http://jmespath.org/)，获取详细信息和示例。
#### `--verbose`
提高日志记录详细程度。 使用 --debug 获取完整的调试日志。
## <a name="azdata-app-template-pull"></a>azdata app template pull
下载指定的 [URL] github 存储库下支持的模板。
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>示例
下载默认模板存储库位置下的所有模板。
```bash
azdata app template pull
```
下载不同存储库位置下的所有模板。
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
按名称下载单个模板。
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>可选参数
#### `--name -n`
模板名称。 有关支持的模板名称的完整列表，运行 `azdata app template list`
#### `--url -u`
指定其他模板存储库位置。 默认： https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
应用程序主干模板的放置位置。
`./templates`
### <a name="global-arguments"></a>全局参数
#### `--debug`
提高日志记录详细程度以显示所有调试日志。
#### `--help -h`
显示此帮助消息并退出。
#### `--output -o`
输出格式。  允许的值：json、jsonc、table、tsv。  默认值：json。
#### `--query -q`
JMESPath 查询字符串。 请参阅 [http://jmespath.org/](http://jmespath.org/)，获取详细信息和示例。
#### `--verbose`
提高日志记录详细程度。 使用 --debug 获取完整的调试日志。

## <a name="next-steps"></a>后续步骤

有关其他 `azdata` 命令的详细信息，请参阅 [azdata 参考](reference-azdata.md)。 有关如何安装 `azdata` 工具的详细信息，请参阅[安装 azdata 以管理 SQL Server 2019 大数据群集](deploy-install-azdata.md)。
