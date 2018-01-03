---
title: "ICorDebugManagedCallback::DebuggerError メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.DebuggerError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc92bc6a1718d9d3505443e5b13786d1a359481f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError メソッド
共通言語ランタイム (CLR) のイベントを処理しようとしているときにエラーが発生したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProcess`  
 [in]イベントが発生したプロセスを表す"ICorDebugProcess"オブジェクトへのポインター。  
  
 `errorHR`  
 [in]イベント ハンドラーから返された HRESULT 値。  
  
 `errorCode`  
 [in]CLR エラーを指定する整数。  
  
## <a name="remarks"></a>コメント  
 プロセスは、エラーの性質によって、パススルーのモードに配置できます。  
  
 `DebugError`コールバックでは、デバッグ サービスが無効になっている、エラーのため、デバッガーは、エラー メッセージを使用できるように、ユーザーを示します。 [Icordebugprocess::getid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)の呼び出しがなど、他のすべてのメソッドを安全[icordebug::terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)、呼び出すことはできません。 デバッガーは、プロセスを終了するためにオペレーティング システムの機能を使用します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
