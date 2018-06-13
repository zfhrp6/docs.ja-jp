---
title: ICorDebugManagedCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c879af682e2d54ed3ae1e9821c0bd85b5cac27d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423092"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback インターフェイス
デバッガーのコールバックを処理するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Break メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|デバッガーに通知時に、<xref:System.Reflection.Emit.OpCodes.Break>コード ストリーム内の命令を実行します。|  
|[Breakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|ブレークポイントが発生したときに、デバッガーに通知します。|  
|[BreakpointSetError メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|共通言語ランタイム (CLR) が正確に関数がジャストでタイム (JIT) コンパイル前に設定されたブレークポイントをバインドできなかったことをデバッガーに通知します。|  
|[ControlCTrap メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|CTRL + C がデバッグ中のプロセスにトラップされることをデバッガーに通知します。|  
|[CreateAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|アプリケーション ドメインが作成されたことをデバッガーに通知します。|  
|[CreateProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|デバッガーは、プロセスをアタッチまたは、最初に起動されたときに通知します。|  
|[CreateThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|スレッドがマネージ コードの実行を開始したことをデバッガーに通知します。|  
|[DebuggerError メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|CLR からのイベントの処理を試行中にエラーが発生したことをデバッガーに通知します。|  
|[EditAndContinueRemap メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|非推奨。 IDE に再割り当てイベントが送信されたことをデバッガーに通知します。|  
|[EvalComplete メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|評価が完了したことをデバッガーに通知します。|  
|[EvalException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|評価版がハンドルされない例外で終了したことをデバッガーに通知します。|  
|[Exception メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|マネージ コードから例外がスローされたことをデバッガーに通知します。|  
|[ExitAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|アプリケーション ドメインが終了していることをデバッガーに通知します。|  
|[ExitProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|プロセスが終了していることをデバッガーに通知します。|  
|[ExitThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|マネージ コードが実行しているスレッドが終了していることをデバッガーに通知します。|  
|[LoadAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|CLR アセンブリが正常に読み込まれたことをデバッガーに通知します。|  
|[LoadClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|クラスが読み込まれたことをデバッガーに通知します。|  
|[LoadModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|CLR モジュールが正常に読み込まれたことをデバッガーに通知します。|  
|[LogMessage メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|CLR マネージ スレッドがという名前のメソッド デバッガーに通知、<xref:System.Diagnostics.EventLog>クラス イベント ログに記録します。|  
|[LogSwitch メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|CLR マネージ スレッドがという名前のメソッド デバッガーに通知、<xref:System.Diagnostics.Switch>クラスを作成、変更、またはデバッグとトレース スイッチを削除します。|  
|[NameChange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|アプリケーション ドメインまたはスレッドのいずれかの名前が変更されたことをデバッガーに通知します。|  
|[StepComplete メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|ステップが完了したことをデバッガーに通知します。|  
|[UnloadAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|CLR アセンブリがアンロードされたことをデバッガーに通知します。|  
|[UnloadClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|クラスがアンロードされることをデバッガーに通知します。|  
|[UnloadModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|CLR モジュール (DLL) がアンロードされたことをデバッガーに通知します。|  
|[UpdateModuleSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|CLR モジュールのシンボルが変更されたことをデバッガーに通知します。|  
  
## <a name="remarks"></a>コメント  
 すべてのコールバックをシリアル化、呼び出され、同一スレッド内、同期された状態では、プロセスと呼ばれます。  
  
 各コールバックの実装を呼び出す必要があります[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)実行を再開します。 場合`ICorDebugController::Continue`を前に、コールバックが返されます、プロセスが停止したままにない複数のイベント コールバックが発生するまでは呼び出されません`ICorDebugController::Continue`と呼びます。  
  
 デバッガーを実装する必要があります[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)場合は、.NET Framework バージョン 2.0 のアプリケーションのデバッグします。 インスタンス`ICorDebugManagedCallback`または`ICorDebugManagedCallback2`するコールバック オブジェクトとして渡される[icordebug::setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)です。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
