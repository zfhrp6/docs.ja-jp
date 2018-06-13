---
title: ICorDebugController::Continue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529a65285203ac831e1bcab9dc1bea69ac28a282
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412566"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue メソッド
呼び出しの後にマネージ スレッドの実行を再開[Stop メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fIsOutOfBand`  
 [in]設定`true`帯域外のイベントから操作を続行する場合がそれ以外の場合に設定`false`です。  
  
## <a name="remarks"></a>コメント  
 `Continue` 呼び出しの後にプロセスを続行、`ICorDebugController::Stop`メソッドです。  
  
 混合モード デバッグを行うときに呼び出すことはありません`Continue`win32 イベント スレッドの帯域外のイベントから続行する場合を除き、します。  
  
 *インバンド イベント*はマネージ イベントまたはデバッガーがプロセスの管理対象の状態との対話をサポートする通常のアンマネージ イベント。 この場合、デバッガーを受け取る、 [icordebugunmanagedcallback::debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)でコールバックの`fOutOfBand`パラメーターに設定`false`です。  
  
 *帯域外のイベント*するプロセスの管理対象の状態との対話は、イベントのため、プロセスの停止中に管理されていないイベントします。 この場合、デバッガーを受け取る、`ICorDebugUnmanagedCallback::DebugEvent`でコールバックの`fOutOfBand`パラメーターに設定`true`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
