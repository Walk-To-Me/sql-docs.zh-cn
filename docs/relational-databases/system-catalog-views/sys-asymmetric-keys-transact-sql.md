---
title: sys. asymmetric_keys （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- asymmetric_keys
- sys.asymmetric_keys_TSQL
- asymmetric_keys_TSQL
- sys.asymmetric_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.asymmetric_keys catalog view
ms.assetid: bbca796a-9bb5-4a62-9ca8-1d255984553d
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c5266b758c965574e7b810804fbbbfd3bb4958ca
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829140"
---
# <a name="sysasymmetric_keys-transact-sql"></a>sys.asymmetric_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  为每个非对称密钥返回一行。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|密钥的名称。 在该数据库中是唯一的。|  
|**principal_id**|**int**|拥有此密钥的数据库主体的 ID。|  
|**asymmetric_key_id**|**int**|密钥的 ID。 在该数据库中是唯一的。|  
|**pvt_key_encryption_type**|**char(2)**|对密钥进行加密的方式。<br /><br /> NA = 未加密<br /><br /> MK = 使用主密钥对密钥进行加密。<br /><br /> PW = 使用用户定义密码对密钥进行加密<br /><br /> SK = 使用服务主密钥对密钥进行加密。|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|对私钥加密方式的说明。<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**指纹**|**varbinary(32)**|密钥的 SHA-1 哈希。 该哈希是全局唯一的。|  
|**算法**|**char(2)**|密钥使用的算法。<br /><br /> 1R = 512 位 RSA<br /><br /> 2R = 1024 位 RSA<br /><br /> 3R = 2048 位 RSA|  
|**algorithm_desc**|**nvarchar(60)**|对密钥所用算法的说明。<br /><br /> RSA_512<br /><br /> RSA_1024<br /><br /> RSA_2048|  
|**key_length**|**int**|密钥的位长度。|  
|**sid**|**varbinary （85）**|该密钥的登录 SID。 对于可扩展密钥管理密钥，此值将为 NULL。|  
|**string_sid**|**nvarchar(128)**|密钥的登录 SID 的字符串表示形式。 对于可扩展密钥管理密钥，此值将为 NULL。|  
|**public_key**|**varbinary(max)**|公钥。|  
|**attested_by**|**nvarchar(260)**|仅供系统使用。|  
|**provider_type**|**nvarchar(120)**|加密提供程序的类型：<br /><br /> CRYPTOGRAPHIC PROVIDER = 可扩展密钥管理密钥<br /><br /> NULL = 非可扩展密钥管理密钥|  
|**cryptographic_provider_guid**|**uniqueidentifier**|加密提供程序的 GUID。 对于非可扩展密钥管理密钥，此值将为 NULL。|  
|**cryptographic_provider_algid**|**sql_variant**|加密提供程序的算法 ID。 对于非可扩展密钥管理密钥，此值将为 NULL。|  
  
## <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;&#40;安全目录视图](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [可扩展的密钥管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Transact-sql&#41;的目录视图 &#40;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
  
  
