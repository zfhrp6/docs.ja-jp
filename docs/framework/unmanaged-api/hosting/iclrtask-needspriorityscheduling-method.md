---
title: ICLRTask::NeedsPriorityScheduling メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36403abcae4d4e691fe6362e61cf7fa979ec7f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435739"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="b91af-102">ICLRTask::NeedsPriorityScheduling メソッド</span><span class="sxs-lookup"><span data-stu-id="b91af-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="b91af-103">再スケジュールの優先度の高いとしてマークするには、スイッチ アウトされる、現在のタスクが必要かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b91af-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b91af-104">構文</span><span class="sxs-lookup"><span data-stu-id="b91af-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b91af-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b91af-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="b91af-106">[out]`true`できるだけ早くです。 それ以外の場合は、タスクの現在のインスタンスを再スケジュールするべきでは、ホストの場合は、`false`です。</span><span class="sxs-lookup"><span data-stu-id="b91af-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b91af-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b91af-107">Return Value</span></span>  
  
|<span data-ttu-id="b91af-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b91af-108">HRESULT</span></span>|<span data-ttu-id="b91af-109">説明</span><span class="sxs-lookup"><span data-stu-id="b91af-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b91af-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b91af-110">S_OK</span></span>|<span data-ttu-id="b91af-111">`NeedsPriorityRescheduling` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="b91af-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="b91af-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b91af-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b91af-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="b91af-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b91af-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b91af-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b91af-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b91af-115">The call timed out.</span></span>|  
|<span data-ttu-id="b91af-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b91af-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b91af-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b91af-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b91af-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b91af-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b91af-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="b91af-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b91af-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b91af-120">E_FAIL</span></span>|<span data-ttu-id="b91af-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b91af-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b91af-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="b91af-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b91af-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="b91af-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b91af-124">コメント</span><span class="sxs-lookup"><span data-stu-id="b91af-124">Remarks</span></span>  
 <span data-ttu-id="b91af-125">CLR がの値を設定するタスクがガベージ コレクターによって収集されるに近い場合は、`pbNeedsPriorityScheduling`に`true`、優先度の高い再スケジューリングを示すです。</span><span class="sxs-lookup"><span data-stu-id="b91af-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="b91af-126">これにより、これにより、ガベージ コレクションで遅延が発生する可能性を最小限に抑えると連携して、メモリ リソースを節約するには、ホストと、ランタイムを有効にすると、タスクを迅速に再スケジュールするホストできます。</span><span class="sxs-lookup"><span data-stu-id="b91af-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b91af-127">要件</span><span class="sxs-lookup"><span data-stu-id="b91af-127">Requirements</span></span>  
 <span data-ttu-id="b91af-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b91af-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91af-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b91af-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b91af-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b91af-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b91af-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b91af-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91af-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b91af-132">See Also</span></span>  
 [<span data-ttu-id="b91af-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b91af-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="b91af-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b91af-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="b91af-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b91af-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="b91af-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b91af-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
