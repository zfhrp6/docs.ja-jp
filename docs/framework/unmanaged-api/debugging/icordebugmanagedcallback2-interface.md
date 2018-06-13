---
title: ICorDebugManagedCallback2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22f4b2cb1bafefefaf3a3fc207af76c80c0c9798
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420343"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 インターフェイス
デバッガーの例外処理およびマネージ デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。 `ICorDebugManagedCallback2` 論理拡張機能は、 [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)インターフェイスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ChangeConnection メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|指定した接続に関連付けられているタスクのセットが変更されたことをデバッガーに通知します。|  
|[CreateConnection メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|新しい接続が作成されたことをデバッガーに通知します。|  
|[DestroyConnection メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|指定された接続が終了したことをデバッガーに通知します。|  
|[Exception メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|例外ハンドラーの検索が開始されたことをデバッガーに通知します。|  
|[ExceptionUnwind メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|例外のアンワインド処理中に状態の通知を提供します。|  
|[FunctionRemapComplete メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|コードの実行を編集された関数の新しいバージョンに切り替えたことをデバッガーに通知します。|  
|[FunctionRemapOpportunity メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|コードの実行が編集された関数の古いバージョンのシーケンス ポイントに達したことをデバッガーに通知します。|  
|[MDANotification メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|コードの実行でマネージ デバッグ アシスタント (MDA) メッセージが発生したことの通知を提供します。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugManagedCallback2`インターフェイスを拡張、`ICorDebugManagedCallback`を .NET Framework version 2.0 で導入された新しいデバッグ イベントを処理するインターフェイスです。  
  
 デバッガーを実装する必要があります`ICorDebugManagedCallback2`場合は、.NET Framework 2.0 アプリケーションのデバッグします。 インスタンス`ICorDebugManagedCallback`または`ICorDebugManagedCallback2`するコールバック オブジェクトとして渡される[icordebug::setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)です。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
