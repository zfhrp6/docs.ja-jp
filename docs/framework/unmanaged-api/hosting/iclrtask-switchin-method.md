---
title: "ICLRTask::SwitchIn メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.SwitchIn
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e99fc43dea70d456bbaab9bba63e5a018e9e9201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="606c8-102">ICLRTask::SwitchIn メソッド</span><span class="sxs-lookup"><span data-stu-id="606c8-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="606c8-103">共通言語ランタイム (CLR) に通知するタスクを現在[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンスを表すは操作可能な状態にします。</span><span class="sxs-lookup"><span data-stu-id="606c8-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="606c8-104">構文</span><span class="sxs-lookup"><span data-stu-id="606c8-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="606c8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="606c8-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="606c8-106">[in]これで、タスクは、現在によって表されます。 物理スレッドへのハンドル`ICLRTask`インスタンスが実行中です。</span><span class="sxs-lookup"><span data-stu-id="606c8-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="606c8-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="606c8-107">Return Value</span></span>  
  
|<span data-ttu-id="606c8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="606c8-108">HRESULT</span></span>|<span data-ttu-id="606c8-109">説明</span><span class="sxs-lookup"><span data-stu-id="606c8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="606c8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="606c8-110">S_OK</span></span>|<span data-ttu-id="606c8-111">`SwitchIn`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="606c8-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="606c8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="606c8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="606c8-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="606c8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="606c8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="606c8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="606c8-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="606c8-115">The call timed out.</span></span>|  
|<span data-ttu-id="606c8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="606c8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="606c8-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="606c8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="606c8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="606c8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="606c8-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="606c8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="606c8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="606c8-120">E_FAIL</span></span>|<span data-ttu-id="606c8-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="606c8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="606c8-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="606c8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="606c8-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="606c8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="606c8-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="606c8-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="606c8-125">`SwitchIn`事前に呼び出したなしで呼び出されました[SwitchOut メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="606c8-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="606c8-126">コメント</span><span class="sxs-lookup"><span data-stu-id="606c8-126">Remarks</span></span>  
 <span data-ttu-id="606c8-127">`threadHandle`パラメーターをタスクは、現在によって表されます。 オペレーティング システム スレッド ハンドルを表す`ICLRTask`インスタンスがスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="606c8-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="606c8-128">このスレッドで偽装が発生した場合は、呼び出す必要があります[ihostsecuritymanager::reverttoself](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)タスクに切り替える前にします。</span><span class="sxs-lookup"><span data-stu-id="606c8-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="606c8-129">呼び出し`SwitchIn`を以前に呼び出さずに`SwitchOut`HOST_E_INVALIDOPERATION の HRESULT 値で失敗します。</span><span class="sxs-lookup"><span data-stu-id="606c8-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="606c8-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="606c8-130">Requirements</span></span>  
 <span data-ttu-id="606c8-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="606c8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="606c8-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="606c8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="606c8-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="606c8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="606c8-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="606c8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="606c8-135">参照</span><span class="sxs-lookup"><span data-stu-id="606c8-135">See Also</span></span>  
 [<span data-ttu-id="606c8-136">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="606c8-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="606c8-137">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="606c8-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="606c8-138">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="606c8-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="606c8-139">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="606c8-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
