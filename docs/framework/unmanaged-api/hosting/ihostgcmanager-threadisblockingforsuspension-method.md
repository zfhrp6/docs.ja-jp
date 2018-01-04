---
title: "IHostGCManager::ThreadIsBlockingForSuspension メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.ThreadIsBlockingForSuspension
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f17e687ebc3d121db36d8fce8b6bd514867a91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="1d196-102">IHostGCManager::ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="1d196-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="1d196-103">メソッドの呼び出し元のスレッドは、ホストに通知のガベージ コレクションをブロックします。</span><span class="sxs-lookup"><span data-stu-id="1d196-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d196-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d196-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1d196-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="1d196-105">Return Value</span></span>  
  
|<span data-ttu-id="1d196-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d196-106">HRESULT</span></span>|<span data-ttu-id="1d196-107">説明</span><span class="sxs-lookup"><span data-stu-id="1d196-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d196-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d196-108">S_OK</span></span>|<span data-ttu-id="1d196-109">`ThreadIsBlockingForSuspension`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="1d196-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="1d196-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d196-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d196-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="1d196-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d196-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d196-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d196-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1d196-113">The call timed out.</span></span>|  
|<span data-ttu-id="1d196-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d196-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d196-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1d196-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d196-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d196-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d196-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="1d196-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d196-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d196-118">E_FAIL</span></span>|<span data-ttu-id="1d196-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1d196-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d196-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1d196-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d196-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="1d196-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d196-122">コメント</span><span class="sxs-lookup"><span data-stu-id="1d196-122">Remarks</span></span>  
 <span data-ttu-id="1d196-123">CLR は呼び出し、通常、`ThreadIsBlockForSuspension`ホスト アンマネージ タスクのスレッドを再スケジュールする機会を提供する、ガベージ コレクションの準備のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="1d196-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d196-124">ホストは、タスクを再スケジュールへの呼び出し後のみ`ThreadIsBlockingForSuspension`です。</span><span class="sxs-lookup"><span data-stu-id="1d196-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="1d196-125">ランタイムの呼び出し後[SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)ホストには、タスクが再スケジュールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d196-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d196-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="1d196-126">Requirements</span></span>  
 <span data-ttu-id="1d196-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1d196-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d196-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d196-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d196-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d196-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d196-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d196-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d196-131">参照</span><span class="sxs-lookup"><span data-stu-id="1d196-131">See Also</span></span>  
 [<span data-ttu-id="1d196-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d196-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1d196-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d196-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1d196-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d196-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1d196-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d196-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="1d196-136">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d196-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
