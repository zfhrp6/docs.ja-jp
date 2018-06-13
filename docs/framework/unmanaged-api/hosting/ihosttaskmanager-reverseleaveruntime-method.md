---
title: IHostTaskManager::ReverseLeaveRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0800a1441b75c5003eabc77793b2b4fa3dd8f0da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444060"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="fbc52-102">IHostTaskManager::ReverseLeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="fbc52-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="fbc52-103">コントロールが共通言語ランタイム (CLR) のままであり、さらに、マネージ コードから呼び出されたアンマネージ関数を入力することをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="fbc52-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc52-104">構文</span><span class="sxs-lookup"><span data-stu-id="fbc52-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fbc52-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="fbc52-105">Return Value</span></span>  
  
|<span data-ttu-id="fbc52-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbc52-106">HRESULT</span></span>|<span data-ttu-id="fbc52-107">説明</span><span class="sxs-lookup"><span data-stu-id="fbc52-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbc52-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbc52-108">S_OK</span></span>|<span data-ttu-id="fbc52-109">`ReverseLeaveRuntime` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="fbc52-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="fbc52-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fbc52-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fbc52-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="fbc52-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fbc52-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fbc52-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fbc52-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="fbc52-113">The call timed out.</span></span>|  
|<span data-ttu-id="fbc52-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fbc52-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fbc52-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="fbc52-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fbc52-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fbc52-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fbc52-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="fbc52-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fbc52-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fbc52-118">E_FAIL</span></span>|<span data-ttu-id="fbc52-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="fbc52-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fbc52-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="fbc52-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fbc52-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="fbc52-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fbc52-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fbc52-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="fbc52-123">十分なメモリが要求されたリソースの割り当てを完了します。</span><span class="sxs-lookup"><span data-stu-id="fbc52-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbc52-124">コメント</span><span class="sxs-lookup"><span data-stu-id="fbc52-124">Remarks</span></span>  
 <span data-ttu-id="fbc52-125">CLR 呼び出し`ReverseLeaveRuntime`プラットフォームを通じてマネージ コードから呼び出された、さらに、アンマネージ関数に制御を呼び出し、現在実行中のタスクを返すことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="fbc52-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="fbc52-126">各呼び出し`ReverseLeaveRuntime`に対応する呼び出しと一致する[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="fbc52-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbc52-127">要件</span><span class="sxs-lookup"><span data-stu-id="fbc52-127">Requirements</span></span>  
 <span data-ttu-id="fbc52-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fbc52-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbc52-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbc52-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbc52-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fbc52-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbc52-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbc52-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc52-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbc52-132">See Also</span></span>  
 [<span data-ttu-id="fbc52-133">CallNeedsHostHook メソッド</span><span class="sxs-lookup"><span data-stu-id="fbc52-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="fbc52-134">EnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="fbc52-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="fbc52-135">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fbc52-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="fbc52-136">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fbc52-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="fbc52-137">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fbc52-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="fbc52-138">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fbc52-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="fbc52-139">LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="fbc52-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="fbc52-140">プラットフォーム呼び出しの詳細</span><span class="sxs-lookup"><span data-stu-id="fbc52-140">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
