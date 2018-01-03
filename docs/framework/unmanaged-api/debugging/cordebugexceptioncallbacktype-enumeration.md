---
title: "CorDebugExceptionCallbackType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionCallbackType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionCallbackType
helpviewer_keywords: CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4efc969395e30dcc237d2ad99c9bc67ee30f4278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a>CorDebugExceptionCallbackType 列挙型
指定されたコールバックの型を示す、 [icordebugmanagedcallback 2::exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)イベント。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|例外がスローされました。|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|例外のワインド プロセスでは、ユーザー コードを入力します。|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|例外ワインド プロセスの検出、`catch`ユーザー コードのブロックです。|  
|`DEBUG_EXCEPTION_UNHANDLED`|例外は処理されませんでした。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
