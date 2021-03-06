---
title: ICorDebugType::GetClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd68df77adafb8b21e7684b28fe978722ca37e16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736791"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass 方法
获取表示未实例化泛型类型 ICorDebugClass 接口指针。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>参数  
 `ppClass`  
 [out]指向的地址的指针`ICorDebugClass`表示未实例化泛型类型的接口。  
  
## <a name="remarks"></a>备注  
 `GetClass` 可以仅在某些情况下调用。 调用[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)然后才能调用`GetClass`。 如果`ICorDebugType::GetType`返回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，CorElementType 值`GetClass`可以调用以获取泛型类型实例化的类型。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
