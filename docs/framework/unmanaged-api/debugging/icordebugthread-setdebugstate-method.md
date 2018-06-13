---
title: ICorDebugThread::SetDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ada120b9cb4100bfadff83d96e0226f911958bf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420766"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState メソッド
この ICorDebugThread のデバッグ状態を記述するフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `state`  
 [in]このスレッドのデバッグ状態を指定する CorDebugThreadState 列挙値のビットごとの組み合わせ。  
  
## <a name="remarks"></a>コメント  
 `SetDebugState` スレッドの現在のデバッグ状態を設定します。 (「現在のデバッグ状態」を表しますデバッグ状態プロセス続行するか、実際の現状ではない場合)。通常この値は、THREAD_RUNNING です。 デバッガーのみ、スレッドのデバッグ状態に影響を与えることができます。 デバッグ状態は最後間で引き続き、THREAD_SUSPENDed で引き続きスレッドを保持する場合は、1 回設定し、その後、ことについて心配する必要ありませんようにします。 スレッドの中断と処理を再開できるは、デッドロック、通常可能性はほとんどありません。 これはスレッドとプロセスの組み込みの品質であり、意図的では。 デバッガーに非同期的に中断でき、デッドロックを中断するスレッドを再開できます。 スレッドのユーザーの状態には、USER_UNSAFE_POINT が含まれている場合、スレッドがガベージ コレクション (GC) をブロックします。 つまり、中断されたスレッドがする可能性が高いデッドロックが発生します。 これには、デバッグ イベントが既にキューには影響可能性があります。 したがって、デバッガーが全体のイベント キューをドレインする必要があります (を呼び出して[icordebugcontroller::hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) 中断またはスレッドを再開する前にします。 それ以外の場合でが既に中断されていると思われるスレッドでイベントを取得することがあります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
