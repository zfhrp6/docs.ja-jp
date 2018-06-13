---
title: ICorDebugThread Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 404f1bdf5865733648084e34a558b7b20a59b3ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423079"
---
# <a name="icordebugthread-interface1"></a>ICorDebugThread Interface1
プロセス内のスレッドを表します。 `ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ClearCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|このメソッドは実装されていません。 使用しないでください。|  
|[CreateEval メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|これに動作する ICorDebugEval オブジェクトを作成`ICorDebugThread`です。|  
|[CreateStepper メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|これで、アクティブなフレームをステップ実行を許可する ICorDebugStepper オブジェクトを作成`ICorDebugThread`です。|  
|[EnumerateChains メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|これですべてのスタック チェーンを含む ICorDebugChainEnum 列挙子へのインターフェイス ポインターを取得`ICorDebugThread`です。|  
|[GetActiveChain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|この active ICorDebugChain へのインターフェイス ポインターを取得`ICorDebugThread`です。|  
|[GetActiveFrame メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|この active ICorDebugFrame へのインターフェイス ポインターを取得`ICorDebugThread`です。|  
|[GetAppDomain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|このアプリケーション ドメインにインターフェイス ポインターを取得`ICorDebugThread`が現在実行中です。|  
|[GetCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|現在、マネージ コードによってスローされる例外を表す ICorDebugValue オブジェクトへのインターフェイス ポインターを取得します。|  
|[GetDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|この現在のデバッグ状態を説明する CorDebugThreadState 値を取得`ICorDebugThread`です。|  
|[GetHandle メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|これのアクティブな部分の現在のハンドルを取得`ICorDebugThread`です。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|これのアクティブな部分の現在のオペレーティング システム識別子を取得`ICorDebugThread`です。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|共通言語ランタイム (CLR) のスレッドにインターフェイス ポインターを取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|このプロセスへのインターフェイス ポインターを取得`ICorDebugThread`一部を形成します。|  
|[GetRegisterSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|これに関連付けられたレジスタ セットへのインターフェイス ポインターを取得`ICorDebugThread`です。|  
|[GetUserState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|この現在の状態を記述する CorDebugUserState 値のビットごとの組み合わせを取得`ICorDebugThread`です。|  
|[SetDebugState メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|ビットごとの組み合わせを設定`CorDebugThreadState`のデバッグ状態を記述する値`ICorDebugThread`です。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
