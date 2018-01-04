---
title: "ICLRDebugManager::SetConnectionTasks メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetConnectionTasks
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f7e47acfcfbde8d5d9724c3a37303f1a584adb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="48642-102">ICLRDebugManager::SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="48642-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="48642-103">リストを関連付けます[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンス識別子とフレンドリ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="48642-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48642-104">構文</span><span class="sxs-lookup"><span data-stu-id="48642-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48642-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48642-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="48642-106">[in]関連付ける接続のホストに固有の識別子、`ppCLRTask`配列。</span><span class="sxs-lookup"><span data-stu-id="48642-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="48642-107">[in]メンバー数`ppCLRTask`です。</span><span class="sxs-lookup"><span data-stu-id="48642-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="48642-108">この番号は 0 より大きい値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48642-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="48642-109">[in]配列`ICLRTask`で識別される、接続に関連付けるへのポインター`id`です。</span><span class="sxs-lookup"><span data-stu-id="48642-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="48642-110">この配列は、少なくとも 1 つのメンバーを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="48642-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48642-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="48642-111">Return Value</span></span>  
  
|<span data-ttu-id="48642-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48642-112">HRESULT</span></span>|<span data-ttu-id="48642-113">説明</span><span class="sxs-lookup"><span data-stu-id="48642-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48642-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="48642-114">S_OK</span></span>|<span data-ttu-id="48642-115">`SetConnectionTasks`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="48642-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="48642-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48642-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48642-117">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="48642-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48642-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48642-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48642-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="48642-119">The call timed out.</span></span>|  
|<span data-ttu-id="48642-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48642-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48642-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="48642-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48642-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48642-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48642-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="48642-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48642-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48642-124">E_FAIL</span></span>|<span data-ttu-id="48642-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="48642-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48642-126">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="48642-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48642-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="48642-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="48642-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="48642-128">E_INVALIDARG</span></span>|<span data-ttu-id="48642-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)が呼び出されていないのは、この値を使用して`id`、または`dwCount`または`id`は 0、1 つの要素の`ppCLRTask`が null です。</span><span class="sxs-lookup"><span data-stu-id="48642-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48642-130">コメント</span><span class="sxs-lookup"><span data-stu-id="48642-130">Remarks</span></span>  
 <span data-ttu-id="48642-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) 3 つのメソッドを提供`BeginConnection`、 `SetConnectionTasks`、および[EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)識別子とフレンドリ名を使用してタスク リストを関連付けるためです。</span><span class="sxs-lookup"><span data-stu-id="48642-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="48642-132">タスクのセットごとに特定の順序では、これら 3 つのメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="48642-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="48642-133">`BeginConnection`新しい接続を確立するためが最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="48642-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="48642-134">`SetConnectionTasks`次に呼び出されたをその接続に関連するタスクのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="48642-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="48642-135">`EndConnection`タスク一覧の識別子とフレンドリ名の間の関連付けを削除する最後に呼び出されます。ただし、異なる接続への呼び出しが入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="48642-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48642-136">必要条件</span><span class="sxs-lookup"><span data-stu-id="48642-136">Requirements</span></span>  
 <span data-ttu-id="48642-137">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="48642-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48642-138">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48642-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48642-139">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="48642-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48642-140">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48642-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48642-141">参照</span><span class="sxs-lookup"><span data-stu-id="48642-141">See Also</span></span>  
 [<span data-ttu-id="48642-142">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48642-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="48642-143">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48642-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="48642-144">BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="48642-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="48642-145">EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="48642-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="48642-146">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48642-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
