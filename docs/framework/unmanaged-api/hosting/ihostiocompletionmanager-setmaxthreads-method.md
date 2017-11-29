---
title: "IHostIoCompletionManager::SetMaxThreads メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 084cbf5509583a45f09bcf903e833f4890c5651e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="0e9eb-102">IHostIoCompletionManager::SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="0e9eb-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="0e9eb-103">I/O 要求を処理するため、ホストに割り当てるスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e9eb-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e9eb-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e9eb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e9eb-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="0e9eb-106">[in]I/O 要求のために割り当てるスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e9eb-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0e9eb-107">Return Value</span></span>  
  
|<span data-ttu-id="0e9eb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e9eb-108">HRESULT</span></span>|<span data-ttu-id="0e9eb-109">説明</span><span class="sxs-lookup"><span data-stu-id="0e9eb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e9eb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e9eb-110">S_OK</span></span>|<span data-ttu-id="0e9eb-111">`SetMaxThreads`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0e9eb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e9eb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e9eb-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e9eb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e9eb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e9eb-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-115">The call timed out.</span></span>|  
|<span data-ttu-id="0e9eb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e9eb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e9eb-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e9eb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e9eb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e9eb-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e9eb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e9eb-120">E_FAIL</span></span>|<span data-ttu-id="0e9eb-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e9eb-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e9eb-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0e9eb-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0e9eb-124">E_NOTIMPL</span></span>|<span data-ttu-id="0e9eb-125">ホストがの実装を提供していない`SetMaxThreads`です。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e9eb-126">コメント</span><span class="sxs-lookup"><span data-stu-id="0e9eb-126">Remarks</span></span>  
 <span data-ttu-id="0e9eb-127">`SetMaxThreads`営業案件の I/O ポート上でのサービス要求に利用できるスレッドの最大数を設定すると、CLR を提供します。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="0e9eb-128">ホストは、スレッド プールのサイズを排他的に制御を実装、パフォーマンス、スケーラビリティなどの理由の必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0e9eb-129">このため、ホストする必要はありません実装`SetMaxThreads`です。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="0e9eb-130">ここでは、ホストは、このメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e9eb-131">要件</span><span class="sxs-lookup"><span data-stu-id="0e9eb-131">Requirements</span></span>  
 <span data-ttu-id="0e9eb-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e9eb-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e9eb-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e9eb-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e9eb-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e9eb-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e9eb-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e9eb-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e9eb-136">See Also</span></span>  
 [<span data-ttu-id="0e9eb-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e9eb-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="0e9eb-138">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e9eb-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
