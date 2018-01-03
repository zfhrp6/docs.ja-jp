---
title: "ICorDebugManagedCallback2::FunctionRemapComplete メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52c7ead9091754d4355880befe6a8a11b3cc5eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a>ICorDebugManagedCallback2::FunctionRemapComplete メソッド
コードの実行を編集された関数の新しいバージョンに切り替えたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]編集済みの関数を含む、アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pThread`  
 [in]リマップ ブレークポイントが発生しました、スレッドを表す ICorDebugThread オブジェクトへのポインター。  
  
 `pFunction`  
 [in]現在のスレッドで実行されている関数のバージョンを表す ICorDebugFunction オブジェクトへのポインター。  
  
## <a name="remarks"></a>コメント  
 このコールバックには、デバッガーを以前に存在していたステッパを再作成する機会が与えられます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
