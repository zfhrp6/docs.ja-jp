---
title: "ICLRSyncManager::CreateRWLockOwnerIterator メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.CreateRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f74a15bb58f0ee62b56204e2b145ae64ff7dd59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="307f5-102">ICLRSyncManager::CreateRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="307f5-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="307f5-103">共通言語ランタイム (CLR) を使用して、一連のリーダー ライター ロックを待機してタスクを決定するホストの反復子を作成するように要求します。</span><span class="sxs-lookup"><span data-stu-id="307f5-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="307f5-104">構文</span><span class="sxs-lookup"><span data-stu-id="307f5-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="307f5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="307f5-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="307f5-106">[in]目的のリーダー ライター ロックに関連付けられているクッキー。</span><span class="sxs-lookup"><span data-stu-id="307f5-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="307f5-107">[out]渡すことができる反復子へのポインター、 [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)と[DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="307f5-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="307f5-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="307f5-108">Return Value</span></span>  
  
|<span data-ttu-id="307f5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="307f5-109">HRESULT</span></span>|<span data-ttu-id="307f5-110">説明</span><span class="sxs-lookup"><span data-stu-id="307f5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="307f5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="307f5-111">S_OK</span></span>|<span data-ttu-id="307f5-112">`CreateRWLockOwnerIterator`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="307f5-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="307f5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="307f5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="307f5-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="307f5-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="307f5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="307f5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="307f5-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="307f5-116">The call timed out.</span></span>|  
|<span data-ttu-id="307f5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="307f5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="307f5-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="307f5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="307f5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="307f5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="307f5-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="307f5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="307f5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="307f5-121">E_FAIL</span></span>|<span data-ttu-id="307f5-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="307f5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="307f5-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="307f5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="307f5-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="307f5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="307f5-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="307f5-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="307f5-126">`CreateRWLockOwnerIterator`マネージ コードを実行している現在のスレッドで呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="307f5-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="307f5-127">コメント</span><span class="sxs-lookup"><span data-stu-id="307f5-127">Remarks</span></span>  
 <span data-ttu-id="307f5-128">ホストの通常の呼び出し、 `CreateRWLockOwnerIterator`、 `DeleteRWLockOwnerIterator`、および`GetRWLockOwnerNext`デッドロックの検出中にメソッドです。</span><span class="sxs-lookup"><span data-stu-id="307f5-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="307f5-129">ホストは、CLR は試みませんのリーダー ライター ロックを維持するためのリーダー ライター ロックがまだ有効であることを保証します。</span><span class="sxs-lookup"><span data-stu-id="307f5-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="307f5-130">いくつかの方法はホストがロックの有効性を確保するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="307f5-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
-   <span data-ttu-id="307f5-131">ホストのリーダー ライター ロックの解放呼び出しをブロックすることができます (たとえば、 [ihostsemaphore::releasesemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) このブロックにデッドロックが発生しないようにしながらです。</span><span class="sxs-lookup"><span data-stu-id="307f5-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
-   <span data-ttu-id="307f5-132">ホストは、このブロックにデッドロックが発生しないことを再確認のリーダー ライター ロックに関連付けられているイベント オブジェクトを待機してから終了をブロックできます。</span><span class="sxs-lookup"><span data-stu-id="307f5-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="307f5-133">`CreateRWLockOwnerIterator`アンマネージ コードを現在実行中のスレッドでのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="307f5-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="307f5-134">必要条件</span><span class="sxs-lookup"><span data-stu-id="307f5-134">Requirements</span></span>  
 <span data-ttu-id="307f5-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="307f5-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="307f5-136">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="307f5-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="307f5-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="307f5-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="307f5-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="307f5-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307f5-139">参照</span><span class="sxs-lookup"><span data-stu-id="307f5-139">See Also</span></span>  
 [<span data-ttu-id="307f5-140">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="307f5-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="307f5-141">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="307f5-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
