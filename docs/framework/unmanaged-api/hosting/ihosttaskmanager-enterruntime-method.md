---
title: "IHostTaskManager::EnterRuntime メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0617ce6960c5afbdad77c28de8284531ae976f3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="c26b1-102">IHostTaskManager::EnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="c26b1-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="c26b1-103">アンマネージ メソッドを呼び出し、プラットフォーム呼び出しメソッドなどに返すこと実行の制御、共通言語ランタイム (CLR) をホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="c26b1-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c26b1-104">構文</span><span class="sxs-lookup"><span data-stu-id="c26b1-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c26b1-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="c26b1-105">Return Value</span></span>  
  
|<span data-ttu-id="c26b1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c26b1-106">HRESULT</span></span>|<span data-ttu-id="c26b1-107">説明</span><span class="sxs-lookup"><span data-stu-id="c26b1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c26b1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c26b1-108">S_OK</span></span>|<span data-ttu-id="c26b1-109">`EnterRuntime`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="c26b1-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="c26b1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c26b1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c26b1-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="c26b1-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c26b1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c26b1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c26b1-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c26b1-113">The call timed out.</span></span>|  
|<span data-ttu-id="c26b1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c26b1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c26b1-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c26b1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c26b1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c26b1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c26b1-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="c26b1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c26b1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c26b1-118">E_FAIL</span></span>|<span data-ttu-id="c26b1-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c26b1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c26b1-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="c26b1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c26b1-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="c26b1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c26b1-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c26b1-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c26b1-123">十分なメモリは、要求された割り当てを完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="c26b1-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c26b1-124">コメント</span><span class="sxs-lookup"><span data-stu-id="c26b1-124">Remarks</span></span>  
 <span data-ttu-id="c26b1-125">`EnterRuntime`ホストに通知するために呼び出されるをアンマネージ関数を事前に呼び出した、 [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)されなかったの実行が完了し、実行時に実行制御を返すメソッド。</span><span class="sxs-lookup"><span data-stu-id="c26b1-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c26b1-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)ホストに通知するために呼び出されるをアンマネージ関数では、対象の事前に呼び出した`LeaveRuntime`が行われた、マネージ コードへの呼び出しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c26b1-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c26b1-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="c26b1-127">Requirements</span></span>  
 <span data-ttu-id="c26b1-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c26b1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c26b1-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c26b1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c26b1-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c26b1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c26b1-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26b1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26b1-132">参照</span><span class="sxs-lookup"><span data-stu-id="c26b1-132">See Also</span></span>  
 [<span data-ttu-id="c26b1-133">高度な COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="c26b1-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="c26b1-134">方法: PInvoke を使用してマネージ コードからネイティブ DLL を呼び出す</span><span class="sxs-lookup"><span data-stu-id="c26b1-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="c26b1-135">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c26b1-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c26b1-136">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c26b1-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c26b1-137">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c26b1-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c26b1-138">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c26b1-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="c26b1-139">LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="c26b1-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
