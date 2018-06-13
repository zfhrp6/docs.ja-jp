---
title: ICorDebugManagedCallback2::MDANotification メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64b09c173e2f66d4c650083cc12f8a0ac2c92007
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417229"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification メソッド
コードが実行されるは、デバッグ中のアプリケーションでマネージ デバッグ アシスタント (MDA) が発生したことの通知を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pController`  
 [in]プロセスを公開する ICorDebugController インターフェイスまたは MDA が発生したアプリケーション ドメインへのポインター。  
  
 デバッガーしないようにコント ローラーは、プロセスまたはアプリケーション ドメイン、かどうかについて、推測に基づいて、判断を行うインターフェイスを常に照会できることができます。  
  
 `pThread`  
 [in]デバッグ イベントが発生したマネージ スレッドを公開する ICorDebugThread インターフェイスへのポインター。  
  
 MDA がアンマネージで発生した場合のスレッドの値`pThread`は null になります。  
  
 オペレーティング システム (OS) のスレッド ID は、MDA オブジェクト自体から取得する必要があります。  
  
 `pMDA`  
 [in]ポインター、 [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA の情報を公開するインターフェイスです。  
  
## <a name="remarks"></a>コメント  
 MDA はヒューリスティック警告であり、呼び出し元を除く任意の明示的なデバッガー アクションは不要[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)デバッグ中は、アプリケーションの実行を再開します。  
  
 Mda が起動され、どのデータが任意の時点で、特定の MDA では、共通言語ランタイム (CLR) を確認できます。 そのため、デバッガーは特定の MDA パターンを必要とするすべての機能を構築する必要があります。  
  
 Mda は、キューに置かれ、MDA が検出された直後後に発生した可能性があります。 これは、ランタイムが検出したときに MDA を発生させるのではなく、MDA を発生させるための安全なポイントに到達するまで待機する必要がある場合に発生する可能性があります。 また、ランタイムは、Mda のキューに置かれたコールバック (「添付」イベントの操作に似ています) の 1 つのセット内の数で発生する可能性があります。  
  
 デバッガーへの参照を解放する必要があります、`ICorDebugMDA`インスタンスから返された後すぐに、 `MDANotification` MDA によって消費されるメモリをリサイクルする CLR のためのコールバック。 多数の Mda が発生している場合、インスタンスを解放するとパフォーマンスが向上する可能性があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
