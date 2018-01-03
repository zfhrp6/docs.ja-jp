---
title: "IHostIoCompletionManager::GetMaxThreads メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d02b0ba4802b72932ea6d23c66153c265a3d6498
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="71ca2-102">IHostIoCompletionManager::GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="71ca2-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>
<span data-ttu-id="71ca2-103">I/O 要求を処理するには、ホストが割り当てることができますのスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="71ca2-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71ca2-104">構文</span><span class="sxs-lookup"><span data-stu-id="71ca2-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71ca2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71ca2-105">Parameters</span></span>  
 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="71ca2-106">[out]ホストが I/O 要求を処理するために割り当てるスレッド プール内のスレッドの最大数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="71ca2-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71ca2-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="71ca2-107">Return Value</span></span>  
  
|<span data-ttu-id="71ca2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71ca2-108">HRESULT</span></span>|<span data-ttu-id="71ca2-109">説明</span><span class="sxs-lookup"><span data-stu-id="71ca2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71ca2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="71ca2-110">S_OK</span></span>|<span data-ttu-id="71ca2-111">`GetMaxThreads`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="71ca2-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="71ca2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71ca2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71ca2-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="71ca2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71ca2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71ca2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71ca2-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="71ca2-115">The call timed out.</span></span>|  
|<span data-ttu-id="71ca2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71ca2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71ca2-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="71ca2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71ca2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71ca2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71ca2-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="71ca2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71ca2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71ca2-120">E_FAIL</span></span>|<span data-ttu-id="71ca2-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="71ca2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71ca2-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="71ca2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71ca2-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="71ca2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="71ca2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="71ca2-124">E_NOTIMPL</span></span>|<span data-ttu-id="71ca2-125">ホストがの実装を提供していない`GetMaxThreads`です。</span><span class="sxs-lookup"><span data-stu-id="71ca2-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71ca2-126">コメント</span><span class="sxs-lookup"><span data-stu-id="71ca2-126">Remarks</span></span>  
 <span data-ttu-id="71ca2-127">ホストには、実装、パフォーマンス、スケーラビリティなどのため、I/O 要求の処理に割り当てることのできるスレッドの数を排他的に制御が必要な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="71ca2-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="71ca2-128">このため、ホストする必要はありません実装`GetMaxThreads`です。</span><span class="sxs-lookup"><span data-stu-id="71ca2-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="71ca2-129">この場合、ホストでは、このメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ca2-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71ca2-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="71ca2-130">Requirements</span></span>  
 <span data-ttu-id="71ca2-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="71ca2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71ca2-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71ca2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71ca2-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="71ca2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71ca2-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ca2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ca2-135">参照</span><span class="sxs-lookup"><span data-stu-id="71ca2-135">See Also</span></span>  
 [<span data-ttu-id="71ca2-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71ca2-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="71ca2-137">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71ca2-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
