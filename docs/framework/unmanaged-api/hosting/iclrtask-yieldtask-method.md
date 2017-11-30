---
title: "ICLRTask::YieldTask メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.YieldTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a02a69329958593aec546ca9c60e3d201ce2a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="2d982-102">ICLRTask::YieldTask メソッド</span><span class="sxs-lookup"><span data-stu-id="2d982-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="2d982-103">共通言語ランタイム (CLR)、確保して、タスクを配置する要求を現在[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンスが表すとプロセッサ時間を他のタスクに使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2d982-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d982-104">構文</span><span class="sxs-lookup"><span data-stu-id="2d982-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2d982-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="2d982-105">Return Value</span></span>  
  
|<span data-ttu-id="2d982-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d982-106">HRESULT</span></span>|<span data-ttu-id="2d982-107">説明</span><span class="sxs-lookup"><span data-stu-id="2d982-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d982-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d982-108">S_OK</span></span>|<span data-ttu-id="2d982-109">`YieldTask`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="2d982-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="2d982-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d982-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d982-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="2d982-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d982-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d982-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d982-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2d982-113">The call timed out.</span></span>|  
|<span data-ttu-id="2d982-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d982-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d982-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2d982-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d982-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d982-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d982-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="2d982-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d982-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d982-118">E_FAIL</span></span>|<span data-ttu-id="2d982-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2d982-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d982-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="2d982-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d982-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="2d982-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d982-122">コメント</span><span class="sxs-lookup"><span data-stu-id="2d982-122">Remarks</span></span>  
 <span data-ttu-id="2d982-123">ホストは`YieldTask`他のタスクまたはプロセスのプロセッサ リソースを要求します。</span><span class="sxs-lookup"><span data-stu-id="2d982-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="2d982-124">このメソッドは CPU 時間を断念する実行時間の長いコードを許可するためのものでは、主にします。</span><span class="sxs-lookup"><span data-stu-id="2d982-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="2d982-125">ランタイムが、タスクを配置しようとしています。 を現在`ICLRTask`処理時間を得ることは成功の保証はありませんが、状態のインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="2d982-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d982-126">要件</span><span class="sxs-lookup"><span data-stu-id="2d982-126">Requirements</span></span>  
 <span data-ttu-id="2d982-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d982-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d982-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d982-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d982-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d982-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d982-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d982-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d982-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d982-131">See Also</span></span>  
 [<span data-ttu-id="2d982-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d982-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2d982-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d982-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2d982-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d982-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2d982-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d982-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
