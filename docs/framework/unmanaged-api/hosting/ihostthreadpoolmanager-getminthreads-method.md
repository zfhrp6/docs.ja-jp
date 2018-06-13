---
title: IHostThreadPoolManager::GetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2064f134d83e6d410e851d8ea9498b45e36aea37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442268"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="b0ca6-102">IHostThreadPoolManager::GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ca6-102">IHostThreadPoolManager::GetMinThreads Method</span></span>
<span data-ttu-id="b0ca6-103">要求に応じるため、スレッド プール内のホストで管理されるアイドル状態スレッド数の最小数を取得します。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-103">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ca6-104">構文</span><span class="sxs-lookup"><span data-stu-id="b0ca6-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0ca6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0ca6-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="b0ca6-106">[out]ホストが現在保持するアイドル状態のワーカー スレッドの最小数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-106">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0ca6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b0ca6-107">Return Value</span></span>  
  
|<span data-ttu-id="b0ca6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0ca6-108">HRESULT</span></span>|<span data-ttu-id="b0ca6-109">説明</span><span class="sxs-lookup"><span data-stu-id="b0ca6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0ca6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0ca6-110">S_OK</span></span>|<span data-ttu-id="b0ca6-111">`GetMinThreads` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b0ca6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b0ca6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b0ca6-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b0ca6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b0ca6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b0ca6-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-115">The call timed out.</span></span>|  
|<span data-ttu-id="b0ca6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0ca6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b0ca6-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b0ca6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b0ca6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b0ca6-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b0ca6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b0ca6-120">E_FAIL</span></span>|<span data-ttu-id="b0ca6-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b0ca6-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b0ca6-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b0ca6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b0ca6-124">E_NOTIMPL</span></span>|<span data-ttu-id="b0ca6-125">ホストがの実装を提供していない`GetMinThreads`です。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0ca6-126">コメント</span><span class="sxs-lookup"><span data-stu-id="b0ca6-126">Remarks</span></span>  
 <span data-ttu-id="b0ca6-127">ホストがの実装を提供する必要はありません`GetMinThreads`です。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-127">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="b0ca6-128">この場合、HRESULT 値 E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ca6-129">要件</span><span class="sxs-lookup"><span data-stu-id="b0ca6-129">Requirements</span></span>  
 <span data-ttu-id="b0ca6-130">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ca6-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b0ca6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0ca6-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0ca6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0ca6-133">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ca6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ca6-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0ca6-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="b0ca6-135">GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ca6-135">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="b0ca6-136">SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ca6-136">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="b0ca6-137">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0ca6-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
