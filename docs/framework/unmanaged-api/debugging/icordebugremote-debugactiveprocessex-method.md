---
title: ICorDebugRemote::DebugActiveProcessEx メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e3cdbff5054ec990c40c333ed4bd4029a91f12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420805"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx メソッド
デバッガーの下でリモート コンピューター上のプロセスを起動します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRemoteTarget`  
 [in]ポインター、 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)です。 このパラメーターは使用、プロセスが実行されているコンピューターを決定します。  
  
 `id`  
 [in]デバッガーのアタッチ先となるプロセスの ID。  
  
 `win32Attach`  
 [in]`true`デバッガーがプロセスの Win32 デバッガーとして動作する必要があります、アンマネージのコールバックのディスパッチ場合はそれ以外の場合、`false`です。  
  
 `ppProcess`  
 [out]デバッガーのアタッチするプロセスを表す"ICorDebugProcess"オブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 リモート コンピューター上のプロセスが正常に接続します。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 リモート コンピューター上のプロセスにアタッチできません。  
  
## <a name="remarks"></a>コメント  
 混合モード デバッグは Silverlight ではサポートされていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugRemote インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
