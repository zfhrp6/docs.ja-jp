---
title: "IHostSyncManager::CreateCrst メソッド"
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
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f932c91892292c787feecf1768c33fb429334bae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="20e08-102">IHostSyncManager::CreateCrst メソッド</span><span class="sxs-lookup"><span data-stu-id="20e08-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="20e08-103">同期のためのクリティカル セクション オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="20e08-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e08-104">構文</span><span class="sxs-lookup"><span data-stu-id="20e08-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20e08-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20e08-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="20e08-106">[out]アドレスへのポインター、 [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス、ホストによって実装された、または null の場合は、クリティカル セクションを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="20e08-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20e08-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="20e08-107">Return Value</span></span>  
  
|<span data-ttu-id="20e08-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20e08-108">HRESULT</span></span>|<span data-ttu-id="20e08-109">説明</span><span class="sxs-lookup"><span data-stu-id="20e08-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20e08-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="20e08-110">S_OK</span></span>|<span data-ttu-id="20e08-111">`CreateCrst`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="20e08-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="20e08-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20e08-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20e08-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="20e08-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20e08-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20e08-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20e08-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="20e08-115">The call timed out.</span></span>|  
|<span data-ttu-id="20e08-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20e08-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20e08-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="20e08-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20e08-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20e08-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20e08-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="20e08-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20e08-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20e08-120">E_FAIL</span></span>|<span data-ttu-id="20e08-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="20e08-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20e08-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="20e08-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20e08-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="20e08-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="20e08-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="20e08-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="20e08-125">十分なメモリは、要求された重要なセクションを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="20e08-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20e08-126">コメント</span><span class="sxs-lookup"><span data-stu-id="20e08-126">Remarks</span></span>  
 <span data-ttu-id="20e08-127">クリティカル セクション オブジェクトは、クリティカル セクションを 1 つのプロセスのスレッドでのみ使用できる点を除いて、ミュー テックス オブジェクトによって提供されるような同期を提供します。</span><span class="sxs-lookup"><span data-stu-id="20e08-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="20e08-128">`CreateCrst`Win32 をミラー化`InitializeCriticalSection`関数。</span><span class="sxs-lookup"><span data-stu-id="20e08-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e08-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="20e08-129">Requirements</span></span>  
 <span data-ttu-id="20e08-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="20e08-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e08-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20e08-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20e08-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="20e08-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20e08-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e08-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e08-134">参照</span><span class="sxs-lookup"><span data-stu-id="20e08-134">See Also</span></span>  
 [<span data-ttu-id="20e08-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20e08-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="20e08-136">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20e08-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="20e08-137">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20e08-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="20e08-138">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20e08-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="20e08-139">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="20e08-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="20e08-140">Semaphore と SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="20e08-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
