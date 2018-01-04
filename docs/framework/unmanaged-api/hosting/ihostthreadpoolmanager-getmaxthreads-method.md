---
title: "IHostThreadPoolManager::GetMaxThreads メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84867f1b5dfdcfd7a50d01c9e51cb0c42da62f0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="0f572-102">IHostThreadPoolManager::GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="0f572-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>
<span data-ttu-id="0f572-103">スレッド プールに同時にホストで管理されるスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="0f572-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f572-104">構文</span><span class="sxs-lookup"><span data-stu-id="0f572-104">Syntax</span></span>  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f572-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f572-105">Parameters</span></span>  
 `pdwMaxWorkerThreads`  
 <span data-ttu-id="0f572-106">[out]ホストがスレッド プールで保持するスレッドの最大数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f572-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f572-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0f572-107">Return Value</span></span>  
  
|<span data-ttu-id="0f572-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f572-108">HRESULT</span></span>|<span data-ttu-id="0f572-109">説明</span><span class="sxs-lookup"><span data-stu-id="0f572-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f572-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f572-110">S_OK</span></span>|<span data-ttu-id="0f572-111">`GetMaxThreads`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0f572-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0f572-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f572-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f572-113">共通言語ランタイム (CLR (をプロセスに読み込まれていないか、CLR は、状態でマネージ コードまたはプロセスの呼び出しは正しく実行されません。</span><span class="sxs-lookup"><span data-stu-id="0f572-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f572-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f572-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f572-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0f572-115">The call timed out.</span></span>|  
|<span data-ttu-id="0f572-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f572-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f572-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0f572-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f572-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f572-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f572-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="0f572-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f572-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f572-120">E_FAIL</span></span>|<span data-ttu-id="0f572-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0f572-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f572-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0f572-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f572-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0f572-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0f572-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0f572-124">E_NOTIMPL</span></span>|<span data-ttu-id="0f572-125">ホストがの実装を提供していない`GetMaxThreads`です。</span><span class="sxs-lookup"><span data-stu-id="0f572-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f572-126">コメント</span><span class="sxs-lookup"><span data-stu-id="0f572-126">Remarks</span></span>  
 <span data-ttu-id="0f572-127">CLR 呼び出し`GetMaxThreads`をスレッド プール内のスレッドの合計数を決定します。</span><span class="sxs-lookup"><span data-stu-id="0f572-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="0f572-128">[GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)メソッドは現在の作業項目を処理していないスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="0f572-128">The [GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="0f572-129">戻り値を超える要求はすべて、`pdwMaxWorkerThreads`パラメーターは、スレッドが使用可能になるまでキューに置かれたままです。</span><span class="sxs-lookup"><span data-stu-id="0f572-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="0f572-130">ホストの実装を提供しない場合`GetMaxThreads`E_NOTIMPL の HRESULT 値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f572-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f572-131">必要条件</span><span class="sxs-lookup"><span data-stu-id="0f572-131">Requirements</span></span>  
 <span data-ttu-id="0f572-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0f572-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f572-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f572-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f572-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0f572-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f572-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f572-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f572-136">参照</span><span class="sxs-lookup"><span data-stu-id="0f572-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="0f572-137">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="0f572-137">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="0f572-138">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="0f572-138">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="0f572-139">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f572-139">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
