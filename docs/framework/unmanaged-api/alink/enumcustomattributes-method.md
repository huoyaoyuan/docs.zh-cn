---
title: EnumCustomAttributes 方法
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09ccf731f0494b6eda49f6a15d04970a723c473b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742060"
---
# <a name="enumcustomattributes-method"></a>EnumCustomAttributes 方法
检索程序集级别自定义属性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a>参数  
 `hEnum`  
 枚举器的句柄。  
  
 `tkType`  
 要枚举的属性的类型。 使用`mdTokenNill`的所有属性。  
  
 `rCustomValues`  
 接收自定义特性标记。  
  
 `cMax`  
 指定的大小`rCustomValues`数组。  
  
 `pcCustomValues`  
 可选择性地接收的令牌值的计数。  
  
## <a name="return-value"></a>返回值  
 如果该方法成功，返回，则为 S_OK。  
  
## <a name="requirements"></a>要求  
 需要 alink.h  
  
## <a name="see-also"></a>请参阅

- [IALink 接口](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 接口](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
