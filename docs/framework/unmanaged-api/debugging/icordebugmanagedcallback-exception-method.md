---
title: "ICorDebugManagedCallback::Exception メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b964f38501822360e6fc63600f7854c9a90f094c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexception-method"></a>ICorDebugManagedCallback::Exception メソッド
マネージ コードから例外がスローされたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]例外がスローされたアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pThread`  
 [in]例外がスローされたスレッドを表す ICorDebugThread オブジェクトへのポインター。  
  
 `unhandled`  
 [in]この値が場合`false`例外がまだそれ以外のアプリケーションによって処理されると、例外が処理されないと、プロセスが終了します。  
  
## <a name="remarks"></a>コメント  
 特定の例外は、スレッド オブジェクトから取得できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
