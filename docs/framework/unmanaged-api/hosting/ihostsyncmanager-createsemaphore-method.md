---
title: "IHostSyncManager::CreateSemaphore メソッド"
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
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d8df29b3eeb565aaa4a977762fcc453fb985e40d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="9a166-102">IHostSyncManager::CreateSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="9a166-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="9a166-103">作成、 [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)待機イベントのセマフォとして使用する共通言語ランタイム (CLR) のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9a166-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a166-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a166-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a166-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a166-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="9a166-106">[in]初期カウント`ppSemaphore`です。</span><span class="sxs-lookup"><span data-stu-id="9a166-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="9a166-107">[in]最大カウント`ppSemaphore`です。</span><span class="sxs-lookup"><span data-stu-id="9a166-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="9a166-108">[out]アドレスへのポインター、`IHostSemaphore`インスタンス、または null の場合、セマフォを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="9a166-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a166-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="9a166-109">Return Value</span></span>  
  
|<span data-ttu-id="9a166-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a166-110">HRESULT</span></span>|<span data-ttu-id="9a166-111">説明</span><span class="sxs-lookup"><span data-stu-id="9a166-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a166-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a166-112">S_OK</span></span>|<span data-ttu-id="9a166-113">`CreateSemaphore`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="9a166-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="9a166-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a166-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a166-115">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="9a166-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a166-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a166-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a166-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9a166-117">The call timed out.</span></span>|  
|<span data-ttu-id="9a166-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a166-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a166-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9a166-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a166-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a166-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a166-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="9a166-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a166-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a166-122">E_FAIL</span></span>|<span data-ttu-id="9a166-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9a166-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a166-124">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9a166-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a166-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="9a166-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a166-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9a166-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9a166-127">十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="9a166-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a166-128">コメント</span><span class="sxs-lookup"><span data-stu-id="9a166-128">Remarks</span></span>  
 <span data-ttu-id="9a166-129">`CreateSemaphore`同じ名前を持つ Win32 関数を反映します。</span><span class="sxs-lookup"><span data-stu-id="9a166-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="9a166-130">`dwInitial`と`dwMax`パラメーターは、セマフォのカウントの同じセマンティクスを使用して、Win32 として`lInitialCount`と`lMaximumCount`パラメーター、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="9a166-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="9a166-131">`dwInitial`0 以上にする必要がありますと`dwMax`、包括的です。</span><span class="sxs-lookup"><span data-stu-id="9a166-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="9a166-132">`dwMax`0 より大きくなければなりません。</span><span class="sxs-lookup"><span data-stu-id="9a166-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a166-133">必要条件</span><span class="sxs-lookup"><span data-stu-id="9a166-133">Requirements</span></span>  
 <span data-ttu-id="9a166-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a166-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a166-135">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a166-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a166-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a166-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a166-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a166-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a166-138">参照</span><span class="sxs-lookup"><span data-stu-id="9a166-138">See Also</span></span>  
 [<span data-ttu-id="9a166-139">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a166-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9a166-140">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a166-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="9a166-141">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a166-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
