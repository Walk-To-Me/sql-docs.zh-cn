---
title: 序列（Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SEQUENCES
- SEQUENCES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SEQUENCES view
- INFORMATION_SCHEMA.SEQUENCES view
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ff8490824c6a0ccb45b383535e830cabff83407
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "77479345"
---
# <a name="sequences-transact-sql"></a>序列（Transact-sql）

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

为当前数据库中当前用户可访问的每个序列返回一行。

若要从这些视图中检索信息，请指定**INFORMATION_SCHEMA**_view_name_的完全限定名称。

|列名称|数据类型|说明|
|-----------------|---------------|-----------------|
|**SEQUENCE_CATALOG**|**nvarchar(128)**|序列限定符|
|**SEQUENCE_SCHEMA**|**nvarchar （** 128） * *|包含序列的架构的名称|
|**SEQUENCE_NAME**|**nvarchar(128)**|序列名称|
|**DATA_TYPE**|**nvarchar （** 128 **）**|序列数据类型|
|**NUMERIC_PRECISION**|**tinyint**|序列的精度|
|**NUMERIC_PRECISION_RADIX**|**smallint**|近似数字数据、精确数字数据、整数数据或货币数据的精度基数。 否则，返回 NULL。|
|**NUMERIC_SCALE**|**int**|近似数字数据、精确数字数据、整数数据或货币数据的小数位数。 否则，返回 NULL。|
|**START_VALUE**|**int**|将由序列对象返回的第一个值。|
|**MINIMUM_VALUE**|**int**|序列对象的边界。 一个新序列对象的默认最小值是该序列对象的数据类型的最小值。 对于 tinyint 数据类型，此值为零，对于所有其他数据类型则为负数。|
|**MAXIMUM_VALUE**|**int**|序列对象的边界。 一个新序列对象的默认最大值是该序列对象的数据类型的最大值。|
|**版本号**|**int**|在每次调用 NEXT VALUE FOR 函数时序列对象值递增（如果为负数，则为递减）的增量。 如果增量是负值，则序列对象为降序，否则为升序。 增量不能为 0。 新序列对象的默认增量为 1。
|**CYCLE_OPTION**|**int**|此属性指定当超过序列对象的最小值或最大值时，序列对象是应从最小值（对于降序序列对象，则为最大值）重新开始，还是应引发异常。 新序列对象的默认循环选项是 NO CYCLE。
|**DECLARED_DATA_TYPE**|**int**|用户定义数据类型的数据类型。|
|**DECLARED_DATA_PRECISION**|**int**|用户定义数据类型的精度。|
|**DECLARED_NUJMERIC_SCALE**|**int**|用户定义数据类型的数值小数位数。|

**示例**下面的示例返回有关测试数据库中的架构的信息：

```sql
SELECT * FROM test.INFORMATION_SCHEMA.SEQUENCES;
```

## <a name="see-also"></a>另请参阅

- [&#40;Transact-sql&#41;的信息架构视图](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)
- [sys.sequences (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md)
