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
ms.openlocfilehash: 11cd8de264a332cd553ad44a35355bf45039ab84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="2c4a2-102">IHostThreadPoolManager::GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="2c4a2-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="2c4a2-103">現在の作業項目を処理していないスレッド プール内のスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c4a2-104">構文</span><span class="sxs-lookup"><span data-stu-id="2c4a2-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c4a2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c4a2-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="2c4a2-106">[out]現在の作業項目を処理していないスレッド プール内のスレッドの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c4a2-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="2c4a2-107">Return Value</span></span>  
  
|<span data-ttu-id="2c4a2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c4a2-108">HRESULT</span></span>|<span data-ttu-id="2c4a2-109">説明</span><span class="sxs-lookup"><span data-stu-id="2c4a2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c4a2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c4a2-110">S_OK</span></span>|<span data-ttu-id="2c4a2-111">`GetAvailableThreads`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2c4a2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c4a2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c4a2-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c4a2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c4a2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c4a2-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-115">The call timed out.</span></span>|  
|<span data-ttu-id="2c4a2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c4a2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c4a2-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c4a2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c4a2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c4a2-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c4a2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c4a2-120">E_FAIL</span></span>|<span data-ttu-id="2c4a2-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c4a2-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c4a2-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2c4a2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2c4a2-124">E_NOTIMPL</span></span>|<span data-ttu-id="2c4a2-125">ホストがの実装を提供していない`GetAvailableThreads`です。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c4a2-126">コメント</span><span class="sxs-lookup"><span data-stu-id="2c4a2-126">Remarks</span></span>  
 <span data-ttu-id="2c4a2-127">ホストの実装を提供しない場合`GetAvailableThreads`E_NOTIMPL の HRESULT 値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c4a2-128">要件</span><span class="sxs-lookup"><span data-stu-id="2c4a2-128">Requirements</span></span>  
 <span data-ttu-id="2c4a2-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c4a2-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c4a2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c4a2-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2c4a2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c4a2-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c4a2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4a2-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c4a2-133">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="2c4a2-134">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c4a2-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
