---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bfdc9d58a86bb4cf945f0c8106bcfc00f3743e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760314"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a>ISymENCUnmanagedMethod::GetFileNameFromOffset 方法
获取与某一偏移量关联的行的文件名称。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>参数  
 `dwOffset`  
 [in]一个`ULONG32`包含的偏移量。  
  
 `cchName`  
 [in]一个`ULONG32`指示的大小`szName`缓冲区。  
  
 `pcchName`  
 [out]一个指向`ULONG32`用于接收大小，以字符为单位，以包含文件名称的缓冲区。  
  
 `szName`  
 [out]包含文件名称的缓冲区。  
  
## <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。  
  
## <a name="requirements"></a>要求  
 **标头：** CorSym.idl CorSym.h  
  
## <a name="see-also"></a>请参阅

- [ISymENCUnmanagedMethod 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
