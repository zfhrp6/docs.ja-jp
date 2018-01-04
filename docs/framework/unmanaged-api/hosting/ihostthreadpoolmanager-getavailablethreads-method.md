---
title: "IHostThreadPoolManager::GetAvailableThreads メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5151b26bad08ef8e1e3c53d649f57f79eb18d03c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="040fa-102">IHostThreadPoolManager::GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="040fa-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="040fa-103">現在の作業項目を処理していないスレッド プール内のスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="040fa-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="040fa-104">構文</span><span class="sxs-lookup"><span data-stu-id="040fa-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="040fa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="040fa-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="040fa-106">[out]現在の作業項目を処理していないスレッド プール内のスレッドの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="040fa-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="040fa-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="040fa-107">Return Value</span></span>  
  
|<span data-ttu-id="040fa-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="040fa-108">HRESULT</span></span>|<span data-ttu-id="040fa-109">説明</span><span class="sxs-lookup"><span data-stu-id="040fa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="040fa-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="040fa-110">S_OK</span></span>|<span data-ttu-id="040fa-111">`GetAvailableThreads`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="040fa-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="040fa-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="040fa-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="040fa-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="040fa-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="040fa-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="040fa-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="040fa-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="040fa-115">The call timed out.</span></span>|  
|<span data-ttu-id="040fa-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="040fa-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="040fa-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="040fa-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="040fa-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="040fa-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="040fa-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="040fa-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="040fa-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="040fa-120">E_FAIL</span></span>|<span data-ttu-id="040fa-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="040fa-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="040fa-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="040fa-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="040fa-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="040fa-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="040fa-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="040fa-124">E_NOTIMPL</span></span>|<span data-ttu-id="040fa-125">ホストがの実装を提供していない`GetAvailableThreads`です。</span><span class="sxs-lookup"><span data-stu-id="040fa-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="040fa-126">コメント</span><span class="sxs-lookup"><span data-stu-id="040fa-126">Remarks</span></span>  
 <span data-ttu-id="040fa-127">ホストの実装を提供しない場合`GetAvailableThreads`E_NOTIMPL の HRESULT 値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="040fa-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="040fa-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="040fa-128">Requirements</span></span>  
 <span data-ttu-id="040fa-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="040fa-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="040fa-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="040fa-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="040fa-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="040fa-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="040fa-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="040fa-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040fa-133">参照</span><span class="sxs-lookup"><span data-stu-id="040fa-133">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="040fa-134">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="040fa-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
