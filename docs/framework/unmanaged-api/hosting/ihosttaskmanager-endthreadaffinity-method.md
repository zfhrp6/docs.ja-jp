---
title: "IHostTaskManager::EndThreadAffinity メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EndThreadAffinity
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b12bdc16d70b9e4ccaecbee1b8bcd4e8f05d59dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="5c7e9-102">IHostTaskManager::EndThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="5c7e9-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="5c7e9-103">マネージ コードをホストが終了する、現在のタスクを別のオペレーティング システム スレッドに移動できない期間を以前の呼び出しに通知[ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c7e9-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c7e9-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5c7e9-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c7e9-105">Return Value</span></span>  
  
|<span data-ttu-id="5c7e9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c7e9-106">HRESULT</span></span>|<span data-ttu-id="5c7e9-107">説明</span><span class="sxs-lookup"><span data-stu-id="5c7e9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c7e9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c7e9-108">S_OK</span></span>|<span data-ttu-id="5c7e9-109">`EndThreadAffinity`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="5c7e9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c7e9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c7e9-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c7e9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c7e9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c7e9-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-113">The call timed out.</span></span>|  
|<span data-ttu-id="5c7e9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c7e9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c7e9-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c7e9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c7e9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c7e9-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c7e9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c7e9-118">E_FAIL</span></span>|<span data-ttu-id="5c7e9-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c7e9-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c7e9-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5c7e9-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="5c7e9-122">E_UNEXPECTED</span></span>|<span data-ttu-id="5c7e9-123">`EndThreadAffinity`対応する以前の呼び出しなしで呼び出されました`BeginThreadAffinity`です。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c7e9-124">コメント</span><span class="sxs-lookup"><span data-stu-id="5c7e9-124">Remarks</span></span>  
 <span data-ttu-id="5c7e9-125">CLR は、対応する呼び出し`BeginThreadAffinity`呼び出す前に現在のタスクで`EndThreadAffinity`です。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="5c7e9-126">このような対応する呼び出しがない場合のホストの実装[IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) E_UNEXPECTED を返し、何もしない必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c7e9-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="5c7e9-127">Requirements</span></span>  
 <span data-ttu-id="5c7e9-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c7e9-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c7e9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c7e9-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c7e9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c7e9-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c7e9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7e9-132">参照</span><span class="sxs-lookup"><span data-stu-id="5c7e9-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="5c7e9-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c7e9-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="5c7e9-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c7e9-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="5c7e9-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c7e9-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="5c7e9-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c7e9-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
