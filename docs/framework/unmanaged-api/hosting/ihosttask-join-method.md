---
title: "IHostTask::Join メソッド"
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
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 85ee44fe9185364a6870b996ca98cfe6cc297bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="6eb4d-102">IHostTask::Join メソッド</span><span class="sxs-lookup"><span data-stu-id="6eb4d-102">IHostTask::Join Method</span></span>
<span data-ttu-id="6eb4d-103">現在で表されるタスクまで呼び出し元のタスクをブロック[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンスが完了すると、指定した時間間隔が経過すると、または[ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)と呼びます。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="6eb4d-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6eb4d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6eb4d-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="6eb4d-106">[in]タスクが終了するまで待機するミリ秒単位の時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="6eb4d-107">この間隔は、タスクが終了する前に経過すると、呼び出し元のタスクがブロック解除します。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="6eb4d-108">[in]1 つ、 [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="6eb4d-109">値 WAIT_ALERTABLE の場合、タスクのスリープを解除するホストに指示`Alert`前に呼び出されます`milliseconds`が経過しました。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eb4d-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="6eb4d-110">Return Value</span></span>  
  
|<span data-ttu-id="6eb4d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6eb4d-111">HRESULT</span></span>|<span data-ttu-id="6eb4d-112">説明</span><span class="sxs-lookup"><span data-stu-id="6eb4d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6eb4d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6eb4d-113">S_OK</span></span>|<span data-ttu-id="6eb4d-114">`Join`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="6eb4d-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6eb4d-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6eb4d-116">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6eb4d-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6eb4d-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6eb4d-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-118">The call timed out.</span></span>|  
|<span data-ttu-id="6eb4d-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6eb4d-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6eb4d-120">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6eb4d-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6eb4d-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6eb4d-122">イベントがキャンセルされましたブロックされたスレッドまたはファイバーがか、または現在待機していた`IHostTask`インスタンスに関連付けられていないタスクです。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="6eb4d-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6eb4d-123">E_FAIL</span></span>|<span data-ttu-id="6eb4d-124">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6eb4d-125">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6eb4d-126">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6eb4d-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="6eb4d-127">Requirements</span></span>  
 <span data-ttu-id="6eb4d-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb4d-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6eb4d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6eb4d-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6eb4d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6eb4d-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb4d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb4d-132">参照</span><span class="sxs-lookup"><span data-stu-id="6eb4d-132">See Also</span></span>  
 [<span data-ttu-id="6eb4d-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6eb4d-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="6eb4d-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6eb4d-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="6eb4d-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6eb4d-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="6eb4d-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6eb4d-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="6eb4d-137">WAIT_OPTION 列挙型</span><span class="sxs-lookup"><span data-stu-id="6eb4d-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
