---
title: "IHostSyncManager::CreateCrstWithSpinCount メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrstWithSpinCount
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41031a5e3d423f0c1d7459250073634592e0291e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="7cffd-102">IHostSyncManager::CreateCrstWithSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="7cffd-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="7cffd-103">同期用のスピン カウントをクリティカル セクション オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7cffd-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cffd-104">構文</span><span class="sxs-lookup"><span data-stu-id="7cffd-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cffd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7cffd-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="7cffd-106">[in]クリティカル セクション オブジェクト用のスピン カウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="7cffd-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="7cffd-107">[out]アドレスへのポインター、 [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス、または null の場合、クリティカル セクションを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="7cffd-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cffd-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7cffd-108">Return Value</span></span>  
  
|<span data-ttu-id="7cffd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7cffd-109">HRESULT</span></span>|<span data-ttu-id="7cffd-110">説明</span><span class="sxs-lookup"><span data-stu-id="7cffd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cffd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7cffd-111">S_OK</span></span>|<span data-ttu-id="7cffd-112">`CreateCrstWithSpinCount`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="7cffd-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="7cffd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7cffd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7cffd-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="7cffd-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7cffd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7cffd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7cffd-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="7cffd-116">The call timed out.</span></span>|  
|<span data-ttu-id="7cffd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7cffd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7cffd-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="7cffd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7cffd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7cffd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7cffd-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="7cffd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7cffd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7cffd-121">E_FAIL</span></span>|<span data-ttu-id="7cffd-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7cffd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7cffd-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="7cffd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7cffd-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="7cffd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7cffd-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7cffd-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7cffd-126">十分なメモリは、要求された重要なセクションを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="7cffd-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cffd-127">コメント</span><span class="sxs-lookup"><span data-stu-id="7cffd-127">Remarks</span></span>  
 <span data-ttu-id="7cffd-128">スピン カウントは、マルチプロセッサ システムでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="7cffd-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="7cffd-129">スピン カウントは、呼び出し元のスレッドが使用できなくなったクリティカル セクションに関連付けられているセマフォでの待機操作を実行する前に回転する必要があります回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="7cffd-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="7cffd-130">クリティカル セクションは、スピン操作中に無料になると、呼び出し元のスレッドは待機操作を回避します。</span><span class="sxs-lookup"><span data-stu-id="7cffd-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="7cffd-131">`CreateCrstWithSpinCount`Win32 をミラー化`InitializeCriticalSectionAndSpinCount`関数。</span><span class="sxs-lookup"><span data-stu-id="7cffd-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cffd-132">要件</span><span class="sxs-lookup"><span data-stu-id="7cffd-132">Requirements</span></span>  
 <span data-ttu-id="7cffd-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7cffd-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cffd-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7cffd-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cffd-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="7cffd-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cffd-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cffd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cffd-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cffd-137">See Also</span></span>  
 [<span data-ttu-id="7cffd-138">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cffd-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="7cffd-139">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cffd-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="7cffd-140">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cffd-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
