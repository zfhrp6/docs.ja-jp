---
title: IHostCrst::SetSpinCount メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d90bce1f693f571a5d5c5d5dca981d09bce59b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438848"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="0e8a1-102">IHostCrst::SetSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="0e8a1-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="0e8a1-103">現在のスピン カウント設定[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e8a1-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e8a1-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e8a1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e8a1-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="0e8a1-106">[in]現在の新しいスピン カウント`IHostCrst`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e8a1-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0e8a1-107">Return Value</span></span>  
  
|<span data-ttu-id="0e8a1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e8a1-108">HRESULT</span></span>|<span data-ttu-id="0e8a1-109">説明</span><span class="sxs-lookup"><span data-stu-id="0e8a1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e8a1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e8a1-110">S_OK</span></span>|<span data-ttu-id="0e8a1-111">`SetSpinCount` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="0e8a1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e8a1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e8a1-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e8a1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e8a1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e8a1-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-115">The call timed out.</span></span>|  
|<span data-ttu-id="0e8a1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e8a1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e8a1-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e8a1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e8a1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e8a1-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e8a1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e8a1-120">E_FAIL</span></span>|<span data-ttu-id="0e8a1-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e8a1-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e8a1-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e8a1-124">コメント</span><span class="sxs-lookup"><span data-stu-id="0e8a1-124">Remarks</span></span>  
 <span data-ttu-id="0e8a1-125">マルチ プロセッサ システム、現在のクリティカル セクションが表されている場合に`IHostCrst`インスタンスではない場合、呼び出し元のスレッドをスピン`dwSpinCount`呼び出しより前に、の時刻[ihostsemaphore::wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)関連付けられているセマフォで重要なセクションです。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="0e8a1-126">クリティカル セクションは、スピン操作中に無料になると、呼び出し元のスレッドは待機操作を回避します。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="0e8a1-127">使用法`dwSpinCount`は Win32 内の同じ名前のパラメーターの使用状況と同じ`InitializeCriticalSectionAndSpinCount`関数。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e8a1-128">要件</span><span class="sxs-lookup"><span data-stu-id="0e8a1-128">Requirements</span></span>  
 <span data-ttu-id="0e8a1-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e8a1-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e8a1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e8a1-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e8a1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e8a1-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e8a1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e8a1-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e8a1-133">See Also</span></span>  
 [<span data-ttu-id="0e8a1-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e8a1-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0e8a1-135">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e8a1-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="0e8a1-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e8a1-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
