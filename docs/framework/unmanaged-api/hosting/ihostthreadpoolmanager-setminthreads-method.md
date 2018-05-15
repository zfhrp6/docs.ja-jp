---
title: IHostThreadPoolManager::SetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f9852034f6d8208bdaa9b424f689adc374bae2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="78f6f-102">IHostThreadPoolManager::SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="78f6f-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="78f6f-103">要求に応じるため、ホストを維持する必要がありますアイドルのスレッドの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="78f6f-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f6f-104">構文</span><span class="sxs-lookup"><span data-stu-id="78f6f-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78f6f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78f6f-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="78f6f-106">[in]ホストが保持する必要がありますのスレッドの新しいの最小数。</span><span class="sxs-lookup"><span data-stu-id="78f6f-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78f6f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="78f6f-107">Return Value</span></span>  
  
|<span data-ttu-id="78f6f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78f6f-108">HRESULT</span></span>|<span data-ttu-id="78f6f-109">説明</span><span class="sxs-lookup"><span data-stu-id="78f6f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78f6f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="78f6f-110">S_OK</span></span>|<span data-ttu-id="78f6f-111">`SetMinThreads` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="78f6f-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="78f6f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78f6f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78f6f-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="78f6f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78f6f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78f6f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78f6f-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="78f6f-115">The call timed out.</span></span>|  
|<span data-ttu-id="78f6f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78f6f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78f6f-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="78f6f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78f6f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78f6f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78f6f-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="78f6f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78f6f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78f6f-120">E_FAIL</span></span>|<span data-ttu-id="78f6f-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="78f6f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78f6f-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="78f6f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78f6f-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="78f6f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="78f6f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="78f6f-124">E_NOTIMPL</span></span>|<span data-ttu-id="78f6f-125">ホストがの実装を提供していない`SetMinThreads`です。</span><span class="sxs-lookup"><span data-stu-id="78f6f-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78f6f-126">コメント</span><span class="sxs-lookup"><span data-stu-id="78f6f-126">Remarks</span></span>  
 <span data-ttu-id="78f6f-127">ホストがの実装を提供する必要はありません`SetMinThreads`です。</span><span class="sxs-lookup"><span data-stu-id="78f6f-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="78f6f-128">この場合、HRESULT 値 E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="78f6f-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f6f-129">要件</span><span class="sxs-lookup"><span data-stu-id="78f6f-129">Requirements</span></span>  
 <span data-ttu-id="78f6f-130">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78f6f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f6f-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78f6f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78f6f-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="78f6f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78f6f-133">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f6f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f6f-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="78f6f-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="78f6f-135">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="78f6f-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="78f6f-136">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="78f6f-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="78f6f-137">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78f6f-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
