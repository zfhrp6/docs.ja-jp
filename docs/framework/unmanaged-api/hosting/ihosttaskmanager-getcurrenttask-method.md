---
title: "IHostTaskManager::GetCurrentTask メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3ba8cbaac28df49a2df70492c1a292ee8cd287e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="d59e8-102">IHostTaskManager::GetCurrentTask メソッド</span><span class="sxs-lookup"><span data-stu-id="d59e8-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="d59e8-103">この呼び出しが行われる元のオペレーティング システムのスレッドで現在実行中のタスクへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d59e8-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59e8-104">構文</span><span class="sxs-lookup"><span data-stu-id="d59e8-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d59e8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d59e8-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="d59e8-106">[out]アドレスへのポインター、 [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)をタスクが現在実行されていない場合、現在実行中のタスク、または null を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d59e8-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d59e8-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d59e8-107">Return Value</span></span>  
  
|<span data-ttu-id="d59e8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d59e8-108">HRESULT</span></span>|<span data-ttu-id="d59e8-109">説明</span><span class="sxs-lookup"><span data-stu-id="d59e8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d59e8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d59e8-110">S_OK</span></span>|<span data-ttu-id="d59e8-111">`GetCurrentTask`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="d59e8-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="d59e8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d59e8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d59e8-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="d59e8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d59e8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d59e8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d59e8-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d59e8-115">The call timed out.</span></span>|  
|<span data-ttu-id="d59e8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d59e8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d59e8-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d59e8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d59e8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d59e8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d59e8-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="d59e8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d59e8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d59e8-120">E_FAIL</span></span>|<span data-ttu-id="d59e8-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d59e8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d59e8-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="d59e8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d59e8-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="d59e8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d59e8-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="d59e8-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="d59e8-125">`GetCurrentTask`ホストの制御範囲外のオペレーティング システム スレッドで呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="d59e8-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d59e8-126">コメント</span><span class="sxs-lookup"><span data-stu-id="d59e8-126">Remarks</span></span>  
 <span data-ttu-id="d59e8-127">ホストの設定もできます、`pTask`を開始しなかったをタスクが CLR を入力することを防ぐために null のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="d59e8-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59e8-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="d59e8-128">Requirements</span></span>  
 <span data-ttu-id="d59e8-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d59e8-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59e8-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d59e8-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d59e8-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d59e8-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d59e8-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59e8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59e8-133">参照</span><span class="sxs-lookup"><span data-stu-id="d59e8-133">See Also</span></span>  
 [<span data-ttu-id="d59e8-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d59e8-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d59e8-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d59e8-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d59e8-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d59e8-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d59e8-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d59e8-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
