---
title: "IHostTaskManager::CallNeedsHostHook メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.CallNeedsHostHook
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0daa122b3576c1a6e6e192a4992549e704721bb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="bfa1f-102">IHostTaskManager::CallNeedsHostHook メソッド</span><span class="sxs-lookup"><span data-stu-id="bfa1f-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="bfa1f-103">共通言語ランタイム (CLR) が指定されたアンマネージ関数呼び出しをインライン展開をできるかどうかを指定するホストを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfa1f-104">構文</span><span class="sxs-lookup"><span data-stu-id="bfa1f-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfa1f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bfa1f-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="bfa1f-106">[in]呼び出されるをアンマネージ関数のマップされたポータブル実行可能 (PE) ファイル内のアドレス。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="bfa1f-107">[out]ホストにフックするへの呼び出しが必要とするかどうかを示すブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfa1f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bfa1f-108">Return Value</span></span>  
  
|<span data-ttu-id="bfa1f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bfa1f-109">HRESULT</span></span>|<span data-ttu-id="bfa1f-110">説明</span><span class="sxs-lookup"><span data-stu-id="bfa1f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bfa1f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bfa1f-111">S_OK</span></span>|<span data-ttu-id="bfa1f-112">`CallNeedsHostHook`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="bfa1f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bfa1f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bfa1f-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bfa1f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bfa1f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bfa1f-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-116">The call timed out.</span></span>|  
|<span data-ttu-id="bfa1f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bfa1f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bfa1f-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bfa1f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bfa1f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bfa1f-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bfa1f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bfa1f-121">E_FAIL</span></span>|<span data-ttu-id="bfa1f-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="bfa1f-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bfa1f-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfa1f-125">コメント</span><span class="sxs-lookup"><span data-stu-id="bfa1f-125">Remarks</span></span>  
 <span data-ttu-id="bfa1f-126">各プラットフォームの分析を実行している CLR コードの実行を最適化するため、呼び出しがインライン展開できるかどうかを決定するコンパイル時に呼び出しを起動します。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="bfa1f-127">`CallNeedsHostHook`アンマネージ関数の呼び出しをフックすることを要求することによってその意思決定を上書きするホストを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="bfa1f-128">フックをホストには、ランタイムは、呼び出しをインライン展開にしません。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="bfa1f-129">通常、ホストは要求フックを浮動小数点の状態を調整する必要がありますまたは呼び出しは、ホストがメモリまたは取得されたロックのランタイムの要求を追跡できない状態になるという通知を受信したとき。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="bfa1f-130">ホストでは、呼び出しをフックすることが必要な場合、ランタイムをホストに通知遷移して、マネージ コードから呼び出しを使用して[EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)、 [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)、 [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)、および[ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfa1f-131">要件</span><span class="sxs-lookup"><span data-stu-id="bfa1f-131">Requirements</span></span>  
 <span data-ttu-id="bfa1f-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfa1f-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bfa1f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfa1f-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bfa1f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfa1f-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfa1f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa1f-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfa1f-136">See Also</span></span>  
 [<span data-ttu-id="bfa1f-137">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfa1f-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="bfa1f-138">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfa1f-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="bfa1f-139">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfa1f-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="bfa1f-140">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfa1f-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
