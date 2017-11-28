---
title: "ICorDebugManagedCallback3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3
helpviewer_keywords: ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2f24cc8fbd8533ef6717bc1dcd1baab0ea9ab45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback3-interface"></a>ICorDebugManagedCallback3 インターフェイス
有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CustomNotification メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|有効なカスタムのデバッガー通知が発生したことを示します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、論理的に拡張、 [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)と[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)インターフェイスです。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
