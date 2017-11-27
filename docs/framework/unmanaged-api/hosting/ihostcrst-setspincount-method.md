---
title: "IHostCrst::SetSpinCount メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.SetSpinCount
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19172c6d498e5066c102c642105d78d10b26212c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="4157d-102">IHostCrst::SetSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="4157d-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="4157d-103">現在のスピン カウント設定[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4157d-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4157d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4157d-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4157d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4157d-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="4157d-106">[in]現在の新しいスピン カウント`IHostCrst`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4157d-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4157d-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="4157d-107">Return Value</span></span>  
  
|<span data-ttu-id="4157d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4157d-108">HRESULT</span></span>|<span data-ttu-id="4157d-109">説明</span><span class="sxs-lookup"><span data-stu-id="4157d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4157d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4157d-110">S_OK</span></span>|<span data-ttu-id="4157d-111">`SetSpinCount`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="4157d-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="4157d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4157d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4157d-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="4157d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4157d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4157d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4157d-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4157d-115">The call timed out.</span></span>|  
|<span data-ttu-id="4157d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4157d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4157d-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4157d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4157d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4157d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4157d-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="4157d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4157d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4157d-120">E_FAIL</span></span>|<span data-ttu-id="4157d-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4157d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4157d-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4157d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4157d-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="4157d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4157d-124">コメント</span><span class="sxs-lookup"><span data-stu-id="4157d-124">Remarks</span></span>  
 <span data-ttu-id="4157d-125">マルチ プロセッサ システム、現在のクリティカル セクションが表されている場合に`IHostCrst`インスタンスではない場合、呼び出し元のスレッドをスピン`dwSpinCount`呼び出しより前に、の時刻[ihostsemaphore::wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)関連付けられているセマフォで重要なセクションです。</span><span class="sxs-lookup"><span data-stu-id="4157d-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="4157d-126">クリティカル セクションは、スピン操作中に無料になると、呼び出し元のスレッドは待機操作を回避します。</span><span class="sxs-lookup"><span data-stu-id="4157d-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="4157d-127">使用法`dwSpinCount`は Win32 内の同じ名前のパラメーターの使用状況と同じ`InitializeCriticalSectionAndSpinCount`関数。</span><span class="sxs-lookup"><span data-stu-id="4157d-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4157d-128">要件</span><span class="sxs-lookup"><span data-stu-id="4157d-128">Requirements</span></span>  
 <span data-ttu-id="4157d-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4157d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4157d-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4157d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4157d-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4157d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4157d-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4157d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4157d-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="4157d-133">See Also</span></span>  
 [<span data-ttu-id="4157d-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4157d-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="4157d-135">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4157d-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="4157d-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4157d-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
