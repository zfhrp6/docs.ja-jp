---
title: "ICorDebug::SetUnmanagedHandler メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c1b6da9db047321583de8c3c9238ed9ad4d4ec6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler メソッド
管理されていないイベントのイベント ハンドラー オブジェクトを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pCallback`  
 [in]ポインター、 [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)アンマネージ イベントのイベント ハンドラーを表すオブジェクト。  
  
## <a name="remarks"></a>コメント  
 イベント ハンドラー オブジェクトのアンマネージ呼び出しの後にイベントを設定する必要があります[icordebug::initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)と呼び出しの前に[icordebug::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)または[icordebug::debugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md). ただし、レガシー目的のため、する必要はありません、最初のネイティブのデバッグ イベントが発生するまで、管理されていないイベントのイベント ハンドラー オブジェクトを設定します。 具体的には場合、 `ICorDebug::CreateProcess` CREATE_SUSPENDED フラグ、メイン スレッドが再開されるまで、イベントをディスパッチできないネイティブのデバッグが設定されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
