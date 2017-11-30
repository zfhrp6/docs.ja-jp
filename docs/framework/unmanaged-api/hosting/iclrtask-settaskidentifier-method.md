---
title: "ICLRTask::SetTaskIdentifier メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.SetTaskIdentifier
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 916f4638ad8206352f3b5973bb6c8b5dab39cda4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="42040-102">ICLRTask::SetTaskIdentifier メソッド</span><span class="sxs-lookup"><span data-stu-id="42040-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="42040-103">共通言語ランタイム (CLR) に指定した id 値を現在のタスクに関連付けるように指示[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="42040-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42040-104">構文</span><span class="sxs-lookup"><span data-stu-id="42040-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42040-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42040-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="42040-106">[in]現在によって表されるタスクに関連付ける、共通言語ランタイムの一意の識別子`ICLRTask`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="42040-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42040-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="42040-107">Return Value</span></span>  
  
|<span data-ttu-id="42040-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42040-108">HRESULT</span></span>|<span data-ttu-id="42040-109">説明</span><span class="sxs-lookup"><span data-stu-id="42040-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42040-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="42040-110">S_OK</span></span>|<span data-ttu-id="42040-111">`SetTaskIdentifier`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="42040-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="42040-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42040-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42040-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="42040-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42040-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42040-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42040-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="42040-115">The call timed out.</span></span>|  
|<span data-ttu-id="42040-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42040-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42040-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="42040-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42040-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42040-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42040-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="42040-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42040-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42040-120">E_FAIL</span></span>|<span data-ttu-id="42040-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="42040-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42040-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="42040-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42040-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="42040-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42040-124">コメント</span><span class="sxs-lookup"><span data-stu-id="42040-124">Remarks</span></span>  
 <span data-ttu-id="42040-125">ホストは、CLR とデバッグ環境でホストを統合するためのタスクに識別子を関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="42040-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="42040-126">識別子には、CLR の意味はありません。</span><span class="sxs-lookup"><span data-stu-id="42040-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="42040-127">CLR を渡しますデバッガー アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="42040-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="42040-128">デバッガーに CLR の呼び出し履歴を関連付けるホスト呼び出し履歴では、この識別子を使用でき、デバッガーのユーザー インターフェイスに表示されるときに統合するには、そのそれぞれトレース情報を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="42040-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42040-129">要件</span><span class="sxs-lookup"><span data-stu-id="42040-129">Requirements</span></span>  
 <span data-ttu-id="42040-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="42040-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42040-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42040-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42040-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="42040-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42040-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42040-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42040-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="42040-134">See Also</span></span>  
 [<span data-ttu-id="42040-135">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42040-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="42040-136">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42040-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="42040-137">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42040-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="42040-138">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42040-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
