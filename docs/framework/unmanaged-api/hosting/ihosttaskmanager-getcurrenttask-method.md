---
title: IHostTaskManager::GetCurrentTask メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2420ddb5cf9be2cfb08f89d27d9aa277305e7ffb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="c1a04-102">IHostTaskManager::GetCurrentTask メソッド</span><span class="sxs-lookup"><span data-stu-id="c1a04-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="c1a04-103">この呼び出しが行われる元のオペレーティング システムのスレッドで現在実行中のタスクへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c1a04-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a04-104">構文</span><span class="sxs-lookup"><span data-stu-id="c1a04-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1a04-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1a04-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="c1a04-106">[out]アドレスへのポインター、 [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)をタスクが現在実行されていない場合、現在実行中のタスク、または null を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="c1a04-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1a04-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="c1a04-107">Return Value</span></span>  
  
|<span data-ttu-id="c1a04-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1a04-108">HRESULT</span></span>|<span data-ttu-id="c1a04-109">説明</span><span class="sxs-lookup"><span data-stu-id="c1a04-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1a04-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1a04-110">S_OK</span></span>|<span data-ttu-id="c1a04-111">`GetCurrentTask` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="c1a04-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="c1a04-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1a04-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1a04-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="c1a04-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1a04-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1a04-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1a04-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c1a04-115">The call timed out.</span></span>|  
|<span data-ttu-id="c1a04-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1a04-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1a04-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c1a04-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1a04-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1a04-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1a04-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="c1a04-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1a04-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1a04-120">E_FAIL</span></span>|<span data-ttu-id="c1a04-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c1a04-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1a04-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="c1a04-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1a04-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="c1a04-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c1a04-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="c1a04-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="c1a04-125">`GetCurrentTask` ホストの制御範囲外のオペレーティング システム スレッドで呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="c1a04-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1a04-126">コメント</span><span class="sxs-lookup"><span data-stu-id="c1a04-126">Remarks</span></span>  
 <span data-ttu-id="c1a04-127">ホストの設定もできます、`pTask`を開始しなかったをタスクが CLR を入力することを防ぐために null のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="c1a04-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a04-128">要件</span><span class="sxs-lookup"><span data-stu-id="c1a04-128">Requirements</span></span>  
 <span data-ttu-id="c1a04-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1a04-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a04-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1a04-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1a04-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1a04-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1a04-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1a04-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a04-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1a04-133">See Also</span></span>  
 [<span data-ttu-id="c1a04-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1a04-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c1a04-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1a04-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c1a04-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1a04-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c1a04-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1a04-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
