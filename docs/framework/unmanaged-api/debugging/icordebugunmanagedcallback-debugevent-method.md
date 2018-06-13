---
title: ICorDebugUnmanagedCallback::DebugEvent メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51ccc7b1b50613f0d2b44a9e101314128782c412
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423131"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent メソッド
ネイティブ イベントが発生したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pDebugEvent`  
 [in]ネイティブ イベントへのポインター。  
  
 `fOutOfBand`  
 [in]`true`デバッガー呼び出すまで、管理されていないイベントの発生後、管理対象プロセスの状態との対話が可能な場合、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)、それ以外の`false`します。  
  
## <a name="remarks"></a>コメント  
 デバッグ中のスレッドが Win32 スレッドの場合は、デバッグのインターフェイス、Win32 のメンバーは使用しません。 呼び出すことができます`ICorDebugController::Continue`Win32 スレッドでのみ、および過去の帯域外のイベントを続行するときのみです。  
  
 `DebugEvent`コールバックがコールバックの標準的な規則に従っていません。 呼び出すと`DebugEvent`プロセスになります、raw、OS デバッグの停止状態。 プロセスは同期されません。 それ以外の入れ子になる可能性があります、マネージ コードに関する情報の要求を満たすために必要な場合に同期済みの状態は自動的に入力`DebugEvent`コールバック。  
  
 呼び出す[icordebugprocess::clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)プロセスを続行する前に、例外イベントを無視するプロセスです。 このメソッドを呼び出すと、要求では、続行、DBG_EXCEPTION_NOT_HANDLED ではなく DBG_CONTINUE を送信し、帯域外のブレークポイントとシングル ステップ例外を自動的にクリアします。 デバッグ中のアプリケーションが停止した場合でも、および未処理の帯域内のイベントが既に存在する場合、帯域外のイベントは、いつでも取得できます。  
  
 .NET framework version 2.0 では、デバッガーを過去の帯域外のブレークポイント イベント続行すぐにする必要があります。 デバッガーを使用する必要があります、 [icordebugprocess 2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)と[icordebugprocess 2::clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)メソッドを追加して、ブレークポイントを削除します。 これらのメソッドは、帯域外のブレークポイントを自動的にスキップされます。 したがって、ディスパッチのみの帯域外のブレークポイントは、Win32 への呼び出しなど、命令ストリーム内に既にある生のブレークポイントをする必要があります`DebugBreak`関数。 使用しないでください`ICorDebugProcess::ClearCurrentException`、 [icordebugprocess::getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)、 [icordebugprocess::setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)、または、他のメンバー、[デバッグ API](../../../../docs/framework/unmanaged-api/debugging/index.md)です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugUnmanagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
