---
title: ICorDebugManagedCallback2::DestroyConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6d4acb7d1156babbd698201c5aea2810644db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="8c0b1-102">ICorDebugManagedCallback2::DestroyConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="8c0b1-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="8c0b1-103">指定された接続が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c0b1-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c0b1-104">Syntax</span></span>  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c0b1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c0b1-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8c0b1-106">[in]破棄された接続を含むプロセスを表す ICorDebugProcess オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="8c0b1-107">[in]破棄された接続の ID。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c0b1-108">コメント</span><span class="sxs-lookup"><span data-stu-id="8c0b1-108">Remarks</span></span>  
 <span data-ttu-id="8c0b1-109">A`DestroyConnection`ホストを呼び出すときに起動されるコールバック[iclrdebugmanager::endconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)で、 [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c0b1-110">要件</span><span class="sxs-lookup"><span data-stu-id="8c0b1-110">Requirements</span></span>  
 <span data-ttu-id="8c0b1-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8c0b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c0b1-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c0b1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c0b1-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c0b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c0b1-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c0b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0b1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c0b1-115">See Also</span></span>  
 [<span data-ttu-id="8c0b1-116">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c0b1-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="8c0b1-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c0b1-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
