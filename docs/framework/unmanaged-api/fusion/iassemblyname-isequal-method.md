---
title: IAssemblyName::IsEqual 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1fc128d15c56981f4bc6122e38e0514d006e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768617"
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual 方法
确定指定[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)对象是否等于此`IAssemblyName`、 根据指定的比较标志。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>参数  
 `pName`  
 [in]`IAssemblyName`要将此对象`IAssemblyName`。  
  
 `dwCmpFlags`  
 [in]按位组合[ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)影响比较的值。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Fusion.h  
  
 **NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IAssemblyName 接口](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [合成枚举](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
