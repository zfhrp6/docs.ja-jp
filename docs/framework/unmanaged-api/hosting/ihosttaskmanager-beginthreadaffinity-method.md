---
title: IHostTaskManager::BeginThreadAffinity メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a94797e6279a1f1d419b977c22d73ca41bbafc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="5d1d2-102">IHostTaskManager::BeginThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="5d1d2-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="5d1d2-103">マネージ コードをホストが、現在のタスクを別のオペレーティング システム スレッドに移動できない期間を入力することを通知します。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d1d2-104">構文</span><span class="sxs-lookup"><span data-stu-id="5d1d2-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5d1d2-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="5d1d2-105">Return Value</span></span>  
  
|<span data-ttu-id="5d1d2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d1d2-106">HRESULT</span></span>|<span data-ttu-id="5d1d2-107">説明</span><span class="sxs-lookup"><span data-stu-id="5d1d2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d1d2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d1d2-108">S_OK</span></span>|<span data-ttu-id="5d1d2-109">`BeginThreadAffinity` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="5d1d2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d1d2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d1d2-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d1d2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d1d2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d1d2-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-113">The call timed out.</span></span>|  
|<span data-ttu-id="5d1d2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d1d2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d1d2-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d1d2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d1d2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d1d2-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d1d2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d1d2-118">E_FAIL</span></span>|<span data-ttu-id="5d1d2-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d1d2-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d1d2-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d1d2-122">コメント</span><span class="sxs-lookup"><span data-stu-id="5d1d2-122">Remarks</span></span>  
 <span data-ttu-id="5d1d2-123">CLR は呼び出し、通常`IHostTaskManager::BeginThreadAffinity`への呼び出しのコンテキストで<xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5d1d2-124">対応する呼び出しがなされるまで、現在のタスクをスケジュールできません必要があります[ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="5d1d2-125">タスクは、out、切り替えることもできますに戻り、交代するときに、スイッチ アウト元となる同じオペレーティング システム スレッドに割り当てる必要があります。呼び出しを入れ子になった`BeginThreadAffinity`がある影響しない、呼び出しが、現在のタスクを参照しているためです。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d1d2-126">要件</span><span class="sxs-lookup"><span data-stu-id="5d1d2-126">Requirements</span></span>  
 <span data-ttu-id="5d1d2-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d1d2-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d1d2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d1d2-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5d1d2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d1d2-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d1d2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1d2-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d1d2-131">See Also</span></span>  
 [<span data-ttu-id="5d1d2-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d1d2-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="5d1d2-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d1d2-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="5d1d2-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d1d2-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="5d1d2-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d1d2-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
