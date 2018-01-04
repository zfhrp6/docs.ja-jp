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
ms.workload: dotnet
ms.openlocfilehash: 6828726fe81cc99adc719659a6eb1b15afda84c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="cb59f-102">IHostSemaphore::ReleaseSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="cb59f-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="cb59f-103">現在のカウントを増やします[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)インスタンスを指定の量。</span><span class="sxs-lookup"><span data-stu-id="cb59f-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb59f-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb59f-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb59f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb59f-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="cb59f-106">[in]現在の数の増加する量`IHostSemaphore`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="cb59f-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="cb59f-107">この量は、0 より大きい値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb59f-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="cb59f-108">[out]前のカウントまたは呼び出し元は、前のカウントを必要としない場合は null へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cb59f-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb59f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="cb59f-109">Return Value</span></span>  
  
|<span data-ttu-id="cb59f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb59f-110">HRESULT</span></span>|<span data-ttu-id="cb59f-111">説明</span><span class="sxs-lookup"><span data-stu-id="cb59f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb59f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb59f-112">S_OK</span></span>|<span data-ttu-id="cb59f-113">`ReleaseSemaphore`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="cb59f-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="cb59f-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb59f-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb59f-115">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="cb59f-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb59f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb59f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb59f-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="cb59f-117">The call timed out.</span></span>|  
|<span data-ttu-id="cb59f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb59f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb59f-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="cb59f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb59f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb59f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb59f-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="cb59f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb59f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb59f-122">E_FAIL</span></span>|<span data-ttu-id="cb59f-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cb59f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb59f-124">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="cb59f-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb59f-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="cb59f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb59f-126">コメント</span><span class="sxs-lookup"><span data-stu-id="cb59f-126">Remarks</span></span>  
 <span data-ttu-id="cb59f-127">CLR は呼び出し、通常`ReleaseSemaphore`これが完了したことの 1 の値を渡すと、リソースを使用して、ホストに通知する、`lReleaseCount`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="cb59f-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb59f-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="cb59f-128">Requirements</span></span>  
 <span data-ttu-id="cb59f-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb59f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb59f-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb59f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb59f-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb59f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb59f-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb59f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb59f-133">参照</span><span class="sxs-lookup"><span data-stu-id="cb59f-133">See Also</span></span>  
 [<span data-ttu-id="cb59f-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb59f-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="cb59f-135">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb59f-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="cb59f-136">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb59f-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="cb59f-137">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb59f-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="cb59f-138">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb59f-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
