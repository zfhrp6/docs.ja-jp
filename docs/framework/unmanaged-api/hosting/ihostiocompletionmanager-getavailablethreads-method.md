---
title: "IHostIoCompletionManager::GetAvailableThreads メソッド"
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
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66f2471e07ae5827d2edb553b4226784b42278c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="0394f-102">IHostIoCompletionManager::GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="0394f-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="0394f-103">されていない要求を処理中、ホストによって管理されるスレッドの合計数の I/O 完了スレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="0394f-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0394f-104">構文</span><span class="sxs-lookup"><span data-stu-id="0394f-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0394f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0394f-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="0394f-106">[out]I/O 完了スレッドのホストによって管理されている現在のサービス要求に利用可能な番号へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0394f-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0394f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0394f-107">Return Value</span></span>  
  
|<span data-ttu-id="0394f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0394f-108">HRESULT</span></span>|<span data-ttu-id="0394f-109">説明</span><span class="sxs-lookup"><span data-stu-id="0394f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0394f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0394f-110">S_OK</span></span>|<span data-ttu-id="0394f-111">`GetAvailableThreads`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0394f-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0394f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0394f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0394f-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="0394f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0394f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0394f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0394f-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0394f-115">The call timed out.</span></span>|  
|<span data-ttu-id="0394f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0394f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0394f-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0394f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0394f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0394f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0394f-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="0394f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0394f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0394f-120">E_FAIL</span></span>|<span data-ttu-id="0394f-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0394f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0394f-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0394f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0394f-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0394f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0394f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0394f-124">E_NOTIMPL</span></span>|<span data-ttu-id="0394f-125">ホストがの実装を提供していない`GetAvailableThreads`です。</span><span class="sxs-lookup"><span data-stu-id="0394f-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0394f-126">コメント</span><span class="sxs-lookup"><span data-stu-id="0394f-126">Remarks</span></span>  
 <span data-ttu-id="0394f-127">ホストは、実装、パフォーマンス、スケーラビリティなどの理由で、I/O 完了スレッド プールのサイズを排他的に制御を必要な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0394f-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0394f-128">そのため、ホストは、実装する必要はありません`GetAvailableThreads`です。</span><span class="sxs-lookup"><span data-stu-id="0394f-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="0394f-129">この場合、ホストでは、このメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0394f-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0394f-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="0394f-130">Requirements</span></span>  
 <span data-ttu-id="0394f-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0394f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0394f-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0394f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0394f-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0394f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0394f-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0394f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0394f-135">参照</span><span class="sxs-lookup"><span data-stu-id="0394f-135">See Also</span></span>  
 [<span data-ttu-id="0394f-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0394f-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="0394f-137">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0394f-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
