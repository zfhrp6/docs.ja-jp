---
title: IHostIoCompletionManager::SetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a810f3a25dc90ddb234c70ca3fa5130039350136
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="b84c1-102">IHostIoCompletionManager::SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="b84c1-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="b84c1-103">I/O 要求を処理するため、ホストに割り当てるスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="b84c1-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b84c1-104">構文</span><span class="sxs-lookup"><span data-stu-id="b84c1-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b84c1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b84c1-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="b84c1-106">[in]I/O 要求のために割り当てるスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="b84c1-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b84c1-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b84c1-107">Return Value</span></span>  
  
|<span data-ttu-id="b84c1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b84c1-108">HRESULT</span></span>|<span data-ttu-id="b84c1-109">説明</span><span class="sxs-lookup"><span data-stu-id="b84c1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b84c1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b84c1-110">S_OK</span></span>|<span data-ttu-id="b84c1-111">`SetMaxThreads` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="b84c1-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b84c1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b84c1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b84c1-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="b84c1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b84c1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b84c1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b84c1-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b84c1-115">The call timed out.</span></span>|  
|<span data-ttu-id="b84c1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b84c1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b84c1-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b84c1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b84c1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b84c1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b84c1-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="b84c1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b84c1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b84c1-120">E_FAIL</span></span>|<span data-ttu-id="b84c1-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b84c1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b84c1-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="b84c1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b84c1-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="b84c1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b84c1-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b84c1-124">E_NOTIMPL</span></span>|<span data-ttu-id="b84c1-125">ホストがの実装を提供していない`SetMaxThreads`です。</span><span class="sxs-lookup"><span data-stu-id="b84c1-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b84c1-126">コメント</span><span class="sxs-lookup"><span data-stu-id="b84c1-126">Remarks</span></span>  
 <span data-ttu-id="b84c1-127">`SetMaxThreads` 営業案件の I/O ポート上でのサービス要求に利用できるスレッドの最大数を設定すると、CLR を提供します。</span><span class="sxs-lookup"><span data-stu-id="b84c1-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="b84c1-128">ホストは、スレッド プールのサイズを排他的に制御を実装、パフォーマンス、スケーラビリティなどの理由の必要があります。</span><span class="sxs-lookup"><span data-stu-id="b84c1-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="b84c1-129">このため、ホストする必要はありません実装`SetMaxThreads`です。</span><span class="sxs-lookup"><span data-stu-id="b84c1-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="b84c1-130">ここでは、ホストは、このメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b84c1-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b84c1-131">要件</span><span class="sxs-lookup"><span data-stu-id="b84c1-131">Requirements</span></span>  
 <span data-ttu-id="b84c1-132">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b84c1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b84c1-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b84c1-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b84c1-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b84c1-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b84c1-135">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b84c1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b84c1-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b84c1-136">See Also</span></span>  
 [<span data-ttu-id="b84c1-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b84c1-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="b84c1-138">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b84c1-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
