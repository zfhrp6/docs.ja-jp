---
title: IHostThreadPoolManager::SetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f978f565dd93eb10a68942fc463f7d5cc212e6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442034"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="3720c-102">IHostThreadPoolManager::SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="3720c-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>
<span data-ttu-id="3720c-103">ホストは、スレッド プールで保持できるスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="3720c-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3720c-104">構文</span><span class="sxs-lookup"><span data-stu-id="3720c-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3720c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3720c-105">Parameters</span></span>  
 `MaxThreads`  
 <span data-ttu-id="3720c-106">スレッド プール内のワーカー スレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="3720c-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3720c-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3720c-107">Return Value</span></span>  
  
|<span data-ttu-id="3720c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3720c-108">HRESULT</span></span>|<span data-ttu-id="3720c-109">説明</span><span class="sxs-lookup"><span data-stu-id="3720c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3720c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3720c-110">S_OK</span></span>|<span data-ttu-id="3720c-111">`SetMaxThreads` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3720c-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="3720c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3720c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3720c-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="3720c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3720c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3720c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3720c-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3720c-115">The call timed out.</span></span>|  
|<span data-ttu-id="3720c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3720c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3720c-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3720c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3720c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3720c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3720c-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="3720c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3720c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3720c-120">E_FAIL</span></span>|<span data-ttu-id="3720c-121">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3720c-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3720c-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="3720c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3720c-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="3720c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3720c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3720c-124">E_NOTIMPL</span></span>|<span data-ttu-id="3720c-125">ホストがの実装を提供していない`SetMaxThreads`です。</span><span class="sxs-lookup"><span data-stu-id="3720c-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3720c-126">コメント</span><span class="sxs-lookup"><span data-stu-id="3720c-126">Remarks</span></span>  
 <span data-ttu-id="3720c-127">ホストは、CLR スレッド プールのサイズを構成するために必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="3720c-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="3720c-128">一部のホストは、実装、パフォーマンス、スケーラビリティなどの理由で、スレッド プールを排他的に制御を必要な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3720c-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="3720c-129">この場合、ホストは、HRESULT 値 E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3720c-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3720c-130">要件</span><span class="sxs-lookup"><span data-stu-id="3720c-130">Requirements</span></span>  
 <span data-ttu-id="3720c-131">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3720c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3720c-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3720c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3720c-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3720c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3720c-134">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3720c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3720c-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="3720c-135">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="3720c-136">GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="3720c-136">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [<span data-ttu-id="3720c-137">SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="3720c-137">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [<span data-ttu-id="3720c-138">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3720c-138">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
