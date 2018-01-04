---
title: "ICLRTask::GetMemStats メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.GetMemStats
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ad5fb2b76ef282258b9a5293b890a19420c1906
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="a43a9-102">ICLRTask::GetMemStats メソッド</span><span class="sxs-lookup"><span data-stu-id="a43a9-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="a43a9-103">タスクに関連する統計のメモリ使用量の情報を取得する現在[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンスが表すです。</span><span class="sxs-lookup"><span data-stu-id="a43a9-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a43a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="a43a9-104">Syntax</span></span>  
  
```  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a43a9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a43a9-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="a43a9-106">[out]ポインター、 [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)割り当てられたバイトの数など、タスクのメモリ使用量に関する詳細が含まれているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="a43a9-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a43a9-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a43a9-107">Return Value</span></span>  
  
|<span data-ttu-id="a43a9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a43a9-108">HRESULT</span></span>|<span data-ttu-id="a43a9-109">説明</span><span class="sxs-lookup"><span data-stu-id="a43a9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a43a9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a43a9-110">S_OK</span></span>|<span data-ttu-id="a43a9-111">`GetMemStats`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a43a9-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="a43a9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a43a9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a43a9-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="a43a9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a43a9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a43a9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a43a9-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a43a9-115">The call timed out.</span></span>|  
|<span data-ttu-id="a43a9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a43a9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a43a9-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a43a9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a43a9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a43a9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a43a9-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="a43a9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a43a9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a43a9-120">E_FAIL</span></span>|<span data-ttu-id="a43a9-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a43a9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a43a9-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a43a9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a43a9-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="a43a9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a43a9-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="a43a9-124">Requirements</span></span>  
 <span data-ttu-id="a43a9-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a43a9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a43a9-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a43a9-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a43a9-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a43a9-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a43a9-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a43a9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a43a9-129">参照</span><span class="sxs-lookup"><span data-stu-id="a43a9-129">See Also</span></span>  
 [<span data-ttu-id="a43a9-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a43a9-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a43a9-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a43a9-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a43a9-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a43a9-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a43a9-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a43a9-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
