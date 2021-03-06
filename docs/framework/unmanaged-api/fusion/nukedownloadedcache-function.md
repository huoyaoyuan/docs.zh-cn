---
title: NukeDownloadedCache 函数
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76ada8400573dd61c25e0dce3f49ce66b5fb30c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773800"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache 函数
删除公共语言运行时 (CLR) 下载缓存。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>返回值  
 此方法返回标准 COM 错误代码，如在 WinError.h 中定义。  
  
## <a name="remarks"></a>备注  
 CLR 下载缓存是从某个 URL 下载强名称的程序集可能重复使用的存储位置的区域。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Fusion.h  
  
 **库：** Fusion.dll 和 Mscorwks.dll。 使用而不是 Mscorwks.dll Fusion.dll 确保面向.NET Framework 的正确版本。  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [CreateHistoryReader 函数](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [GetHistoryFileDirectory 函数](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [合成全局静态函数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
