---
title: ICLRDebugManager::EndConnection メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58ce0389c77b6534cbbf37fe985f89c187065df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435826"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="c8bed-102">ICLRDebugManager::EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="c8bed-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="c8bed-103">タスクの一覧、識別子、およびフレンドリ名の間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="c8bed-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8bed-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8bed-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8bed-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8bed-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="c8bed-106">[in]接続と、関連付けられている共通言語ランタイム (CLR) タスクの一覧のホストに固有の識別子です。</span><span class="sxs-lookup"><span data-stu-id="c8bed-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8bed-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="c8bed-107">Return Value</span></span>  
  
|<span data-ttu-id="c8bed-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8bed-108">HRESULT</span></span>|<span data-ttu-id="c8bed-109">説明</span><span class="sxs-lookup"><span data-stu-id="c8bed-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8bed-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8bed-110">S_OK</span></span>|<span data-ttu-id="c8bed-111">`EndConnection` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="c8bed-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="c8bed-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8bed-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8bed-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="c8bed-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8bed-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8bed-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8bed-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c8bed-115">The call timed out.</span></span>|  
|<span data-ttu-id="c8bed-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8bed-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8bed-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c8bed-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8bed-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8bed-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8bed-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="c8bed-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8bed-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8bed-120">E_FAIL</span></span>|<span data-ttu-id="c8bed-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c8bed-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8bed-122">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="c8bed-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8bed-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="c8bed-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c8bed-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c8bed-124">E_INVALIDARG</span></span>|<span data-ttu-id="c8bed-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)を使用して呼び出されませんでした`dwConnectionId`、または`dwConnectionId`は 0 でした。</span><span class="sxs-lookup"><span data-stu-id="c8bed-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8bed-126">コメント</span><span class="sxs-lookup"><span data-stu-id="c8bed-126">Remarks</span></span>  
 <span data-ttu-id="c8bed-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) 3 つのメソッドを提供`BeginConnection`、 [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)、および`EndConnection`識別子とフレンドリ名を使用してタスク リストを関連付けるためです。</span><span class="sxs-lookup"><span data-stu-id="c8bed-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8bed-128">タスクのセットごとに特定の順序では、これら 3 つのメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8bed-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="c8bed-129">`BeginConnection` 新しい接続を確立するためが最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c8bed-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="c8bed-130">`SetConnectionTasks` 次に呼び出されたをその接続に関連するタスクのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="c8bed-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="c8bed-131">`EndConnection` タスク一覧の識別子とフレンドリ名の間の関連付けを削除する最後に呼び出されます。ただし、異なる接続への呼び出しが入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c8bed-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8bed-132">要件</span><span class="sxs-lookup"><span data-stu-id="c8bed-132">Requirements</span></span>  
 <span data-ttu-id="c8bed-133">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8bed-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8bed-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8bed-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8bed-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c8bed-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8bed-136">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8bed-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8bed-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8bed-137">See Also</span></span>  
 [<span data-ttu-id="c8bed-138">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8bed-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c8bed-139">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8bed-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="c8bed-140">BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="c8bed-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="c8bed-141">SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="c8bed-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="c8bed-142">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8bed-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
