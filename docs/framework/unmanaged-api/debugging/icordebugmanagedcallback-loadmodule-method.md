---
title: "ICorDebugManagedCallback::LoadModule メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LoadModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d17001db68043f5d46a90738a8ad3e0635de762
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>ICorDebugManagedCallback::LoadModule メソッド
共通言語ランタイム (CLR) モジュールが正常に読み込まれたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]ICorDebugAppDomain を表すオブジェクトをモジュールが読み込まれて、アプリケーション ドメインへのポインター。  
  
 `pModule`  
 [in]CLR モジュールを表す ICorDebugModule オブジェクトへのポインター。  
  
## <a name="remarks"></a>コメント  
 `LoadModule`コールバックは、モジュールのメタデータを調べて、・ イン タイム (JIT) コンパイラ フラグを設定または有効または無効にクラス、モジュールのコールバックを読み込み適切な時間を提供します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [UnloadModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
