---
title: "IHostSemaphore::ReleaseSemaphore メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore.ReleaseSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06765d019d5443730656e7f4d6745bd8ad39ee00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="54123-102">IHostSemaphore::ReleaseSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="54123-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="54123-103">現在のカウントを増やします[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)インスタンスを指定の量。</span><span class="sxs-lookup"><span data-stu-id="54123-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54123-104">構文</span><span class="sxs-lookup"><span data-stu-id="54123-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54123-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="54123-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="54123-106">[in]現在の数の増加する量`IHostSemaphore`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="54123-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="54123-107">この量は、0 より大きい値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="54123-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="54123-108">[out]前のカウントまたは呼び出し元は、前のカウントを必要としない場合は null へのポインター。</span><span class="sxs-lookup"><span data-stu-id="54123-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54123-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="54123-109">Return Value</span></span>  
  
|<span data-ttu-id="54123-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54123-110">HRESULT</span></span>|<span data-ttu-id="54123-111">説明</span><span class="sxs-lookup"><span data-stu-id="54123-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54123-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="54123-112">S_OK</span></span>|<span data-ttu-id="54123-113">`ReleaseSemaphore`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="54123-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="54123-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54123-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54123-115">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="54123-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54123-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54123-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54123-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="54123-117">The call timed out.</span></span>|  
|<span data-ttu-id="54123-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54123-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54123-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="54123-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54123-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54123-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54123-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="54123-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54123-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54123-122">E_FAIL</span></span>|<span data-ttu-id="54123-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="54123-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54123-124">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="54123-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54123-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="54123-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54123-126">コメント</span><span class="sxs-lookup"><span data-stu-id="54123-126">Remarks</span></span>  
 <span data-ttu-id="54123-127">CLR は呼び出し、通常`ReleaseSemaphore`これが完了したことの 1 の値を渡すと、リソースを使用して、ホストに通知する、`lReleaseCount`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="54123-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54123-128">要件</span><span class="sxs-lookup"><span data-stu-id="54123-128">Requirements</span></span>  
 <span data-ttu-id="54123-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="54123-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54123-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54123-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54123-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="54123-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54123-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54123-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54123-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="54123-133">See Also</span></span>  
 [<span data-ttu-id="54123-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54123-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="54123-135">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54123-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="54123-136">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54123-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="54123-137">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54123-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="54123-138">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54123-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
