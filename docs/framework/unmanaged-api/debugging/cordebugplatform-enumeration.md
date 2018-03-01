---
title: "CorDebugPlatform 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1f67ed6ad886c137eddaa42840f3f0edda88bd4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugplatform-enumeration"></a>CorDebugPlatform 列挙型
使用されるターゲット プラットフォームの値を提供、 [icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|ターゲット プラットフォームは、Intel x86 ハードウェア上で稼動する Windows です。|  
|CORDB_PLATFORM_WINDOWS_AMD64|ターゲット プラットフォームは、AMD64 または Intel EM64T ハードウェア上で稼動する 64 ビット Windows です。|  
|CORDB_PLATFORM_WINDOWS_IA64|ターゲット プラットフォームは、Intel IA-64 ハードウェア上で稼動する 32 ビット Windows です。|  
|CORDB_PLATFORM_MAC_PPC|ターゲット プラットフォームは、PowerPC ハードウェア上で稼動する Macintosh オペレーティング システムです。|  
|CORDB_PLATFORM_MAC_X86|ターゲット プラットフォームは、Intel x86 ハードウェア上で稼動する Macintosh オペレーティング システムです。|  
|CORDB_PLATFORM_WINDOWS_ARM|ターゲット プラットフォームは、Windows ARM ハードウェア上で稼動する Macintosh オペレーティング システムです。|  
|CORDB_PLATFORM_MAC_AMD64|ターゲット プラットフォームは、amd 64 ハードウェアで実行されている Macintosh オペレーティング システムです。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 `CORDB_PLATFORM_WINDOWS_ARM` および `CORDB_PLATFORM_MAC_AMD64` メンバーは、.NET Framework 4.5.2 以降のバージョンでのみ使用できます。  
  
## <a name="see-also"></a>参照  
 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
