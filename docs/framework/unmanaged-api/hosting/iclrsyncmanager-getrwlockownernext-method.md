---
title: "ICLRSyncManager::GetRWLockOwnerNext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetRWLockOwnerNext
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8551a6981efd1005f5433c8c862623766bf838f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="523a1-102">ICLRSyncManager::GetRWLockOwnerNext メソッド</span><span class="sxs-lookup"><span data-stu-id="523a1-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="523a1-103">次の取得[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)現在のリーダー ライター ロックでブロックされているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="523a1-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="523a1-104">構文</span><span class="sxs-lookup"><span data-stu-id="523a1-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="523a1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="523a1-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="523a1-106">[in]反復子への呼び出しを使用して作成された[CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="523a1-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="523a1-107">[out]ポインター`IHostTask`タスクが待機していない場合、ロック、または null でを待機中です。</span><span class="sxs-lookup"><span data-stu-id="523a1-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="523a1-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="523a1-108">Return Value</span></span>  
  
|<span data-ttu-id="523a1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="523a1-109">HRESULT</span></span>|<span data-ttu-id="523a1-110">説明</span><span class="sxs-lookup"><span data-stu-id="523a1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="523a1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="523a1-111">S_OK</span></span>|<span data-ttu-id="523a1-112">`GetRWLockOwnerNext`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="523a1-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="523a1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="523a1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="523a1-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="523a1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="523a1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="523a1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="523a1-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="523a1-116">The call timed out.</span></span>|  
|<span data-ttu-id="523a1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="523a1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="523a1-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="523a1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="523a1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="523a1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="523a1-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="523a1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="523a1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="523a1-121">E_FAIL</span></span>|<span data-ttu-id="523a1-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="523a1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="523a1-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="523a1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="523a1-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="523a1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="523a1-125">コメント</span><span class="sxs-lookup"><span data-stu-id="523a1-125">Remarks</span></span>  
 <span data-ttu-id="523a1-126">場合`ppOwnerHostTask`に設定されている null、イテレーションが終了し、ホストを呼び出す必要があります、 [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="523a1-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="523a1-127">CLR 呼び出し`AddRef`上、`IHostTask`する`ppOwnerHostTask`ホストは、ポインターを保持しているときに、このタスクが終了されないようにするへのポインター。</span><span class="sxs-lookup"><span data-stu-id="523a1-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="523a1-128">ホストを呼び出す必要があります`Release`が完了すると、参照カウントをデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="523a1-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="523a1-129">要件</span><span class="sxs-lookup"><span data-stu-id="523a1-129">Requirements</span></span>  
 <span data-ttu-id="523a1-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="523a1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="523a1-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="523a1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="523a1-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="523a1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="523a1-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="523a1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523a1-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="523a1-134">See Also</span></span>  
 [<span data-ttu-id="523a1-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="523a1-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="523a1-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="523a1-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
