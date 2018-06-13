---
title: ICLRTask::SwitchOut メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 118aa3820f422941bea1707dbf7eef2a85027eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439673"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="c1aa7-102">ICLRTask::SwitchOut メソッド</span><span class="sxs-lookup"><span data-stu-id="c1aa7-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="c1aa7-103">現在のタスクが表す共通言語ランタイム (CLR) に通知[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンスは操作可能な状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1aa7-104">構文</span><span class="sxs-lookup"><span data-stu-id="c1aa7-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c1aa7-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="c1aa7-105">Return Value</span></span>  
  
|<span data-ttu-id="c1aa7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1aa7-106">HRESULT</span></span>|<span data-ttu-id="c1aa7-107">説明</span><span class="sxs-lookup"><span data-stu-id="c1aa7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1aa7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1aa7-108">S_OK</span></span>|<span data-ttu-id="c1aa7-109">`SwitchOut` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="c1aa7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1aa7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1aa7-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1aa7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1aa7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1aa7-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-113">The call timed out.</span></span>|  
|<span data-ttu-id="c1aa7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1aa7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1aa7-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1aa7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1aa7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1aa7-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1aa7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1aa7-118">E_FAIL</span></span>|<span data-ttu-id="c1aa7-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1aa7-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1aa7-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1aa7-122">コメント</span><span class="sxs-lookup"><span data-stu-id="c1aa7-122">Remarks</span></span>  
 <span data-ttu-id="c1aa7-123">ホストは`SwitchOut`いるタスクの実行が一時的に停止して CLR に通知を現在`ICLRTask`インスタンスが表す、およびタスクをスケジュールし直されます。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1aa7-124">要件</span><span class="sxs-lookup"><span data-stu-id="c1aa7-124">Requirements</span></span>  
 <span data-ttu-id="c1aa7-125">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1aa7-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1aa7-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1aa7-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1aa7-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1aa7-128">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1aa7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1aa7-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1aa7-129">See Also</span></span>  
 [<span data-ttu-id="c1aa7-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1aa7-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c1aa7-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1aa7-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c1aa7-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1aa7-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c1aa7-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1aa7-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
