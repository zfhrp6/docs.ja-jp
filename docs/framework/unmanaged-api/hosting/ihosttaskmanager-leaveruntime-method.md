---
title: IHostTaskManager::LeaveRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d31c5c1b95d250f90b202b391d908f9c12afb84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444478"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="e38fb-102">IHostTaskManager::LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="e38fb-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="e38fb-103">現在実行中のタスクが共通言語ランタイム (CLR) のままにし、アンマネージ コードの入力があるホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e38fb-104">対応する呼び出し[ihosttaskmanager::enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)現在実行中のタスクがマネージ コードを再入力するホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e38fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="e38fb-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e38fb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e38fb-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="e38fb-107">[in]アンマネージ関数を呼び出すのマップされたポータブル実行可能ファイル内のアドレス。</span><span class="sxs-lookup"><span data-stu-id="e38fb-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e38fb-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e38fb-108">Return Value</span></span>  
  
|<span data-ttu-id="e38fb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e38fb-109">HRESULT</span></span>|<span data-ttu-id="e38fb-110">説明</span><span class="sxs-lookup"><span data-stu-id="e38fb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e38fb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e38fb-111">S_OK</span></span>|<span data-ttu-id="e38fb-112">`LeaveRuntime` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="e38fb-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="e38fb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e38fb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e38fb-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e38fb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e38fb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e38fb-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e38fb-116">The call timed out.</span></span>|  
|<span data-ttu-id="e38fb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e38fb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e38fb-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e38fb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e38fb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e38fb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e38fb-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="e38fb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e38fb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e38fb-121">E_FAIL</span></span>|<span data-ttu-id="e38fb-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e38fb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e38fb-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e38fb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e38fb-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e38fb-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e38fb-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e38fb-126">十分なメモリがある要求の割り当てを完了します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e38fb-127">コメント</span><span class="sxs-lookup"><span data-stu-id="e38fb-127">Remarks</span></span>  
 <span data-ttu-id="e38fb-128">アンマネージ コードとの間の呼び出しシーケンスは、入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e38fb-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="e38fb-129">たとえば、次の表に仮想的な状況への呼び出しのシーケンス`LeaveRuntime`、 [ihosttaskmanager::reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)、 [ihosttaskmanager::reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)、および`IHostTaskManager::EnterRuntime`ホストが入れ子になったレイヤーを特定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e38fb-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="e38fb-130">アクション</span><span class="sxs-lookup"><span data-stu-id="e38fb-130">Action</span></span>|<span data-ttu-id="e38fb-131">対応するメソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="e38fb-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="e38fb-132">マネージ Visual Basic 実行可能なプラットフォームを使用して、C で記述されたアンマネージ関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="e38fb-133">アンマネージ C 関数は、c# で記述されたマネージ DLL でメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="e38fb-134">C# の場合、マネージ関数が C で記述された別のアンマネージ関数を呼び出してもプラットフォーム呼び出しを使用します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="e38fb-135">2 番目のアンマネージ関数では、c# 関数への実行を返します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="e38fb-136">C# 関数は、最初のアンマネージ関数に実行を返します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="e38fb-137">1 つ目のアンマネージ関数では、Visual Basic プログラムに実行を返します。</span><span class="sxs-lookup"><span data-stu-id="e38fb-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="e38fb-138">要件</span><span class="sxs-lookup"><span data-stu-id="e38fb-138">Requirements</span></span>  
 <span data-ttu-id="e38fb-139">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e38fb-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e38fb-140">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e38fb-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e38fb-141">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e38fb-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e38fb-142">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e38fb-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e38fb-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="e38fb-143">See Also</span></span>  
 [<span data-ttu-id="e38fb-144">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e38fb-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e38fb-145">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e38fb-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e38fb-146">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e38fb-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e38fb-147">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e38fb-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
