---
title: IHostControl::GetHostManager メソッド
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 355d2e259adb13da44b09e19872337c17ac20ade
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="e97b2-102">IHostControl::GetHostManager メソッド</span><span class="sxs-lookup"><span data-stu-id="e97b2-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="e97b2-103">指定したホストのインターフェイスの実装へのインターフェイス ポインターを取得`IID`です。</span><span class="sxs-lookup"><span data-stu-id="e97b2-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97b2-104">構文</span><span class="sxs-lookup"><span data-stu-id="e97b2-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e97b2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e97b2-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="e97b2-106">[in]`IID`インターフェイスの共通言語ランタイム (CLR) のクエリを実行するのです。</span><span class="sxs-lookup"><span data-stu-id="e97b2-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="e97b2-107">[out]ホスト実装インターフェイス、または、ホストがこのインターフェイスをサポートしていない場合は null へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e97b2-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e97b2-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e97b2-108">Return Value</span></span>  
  
|<span data-ttu-id="e97b2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e97b2-109">HRESULT</span></span>|<span data-ttu-id="e97b2-110">説明</span><span class="sxs-lookup"><span data-stu-id="e97b2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e97b2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e97b2-111">S_OK</span></span>|<span data-ttu-id="e97b2-112">`GetHostManager` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="e97b2-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="e97b2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e97b2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e97b2-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="e97b2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e97b2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e97b2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e97b2-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e97b2-116">The call timed out.</span></span>|  
|<span data-ttu-id="e97b2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e97b2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e97b2-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e97b2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e97b2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e97b2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e97b2-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="e97b2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e97b2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e97b2-121">E_FAIL</span></span>|<span data-ttu-id="e97b2-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e97b2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e97b2-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e97b2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e97b2-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="e97b2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e97b2-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e97b2-125">E_INVALIDARG</span></span>|<span data-ttu-id="e97b2-126">要求された`IID`が無効です。</span><span class="sxs-lookup"><span data-stu-id="e97b2-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="e97b2-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="e97b2-127">E_NOINTERFACE</span></span>|<span data-ttu-id="e97b2-128">要求されたインターフェイスがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e97b2-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e97b2-129">コメント</span><span class="sxs-lookup"><span data-stu-id="e97b2-129">Remarks</span></span>  
 <span data-ttu-id="e97b2-130">CLR では、次のインターフェイスの 1 つ以上をサポートするかどうかを決定するホストを照会します。</span><span class="sxs-lookup"><span data-stu-id="e97b2-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
-   [<span data-ttu-id="e97b2-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [<span data-ttu-id="e97b2-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [<span data-ttu-id="e97b2-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [<span data-ttu-id="e97b2-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [<span data-ttu-id="e97b2-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [<span data-ttu-id="e97b2-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [<span data-ttu-id="e97b2-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [<span data-ttu-id="e97b2-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [<span data-ttu-id="e97b2-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="e97b2-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="e97b2-140">ホストは、指定されたインターフェイスをサポートする場合は設定`ppObject`そのインターフェイスの実装にします。</span><span class="sxs-lookup"><span data-stu-id="e97b2-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="e97b2-141">それ以外の場合、設定`ppObject`を null にします。</span><span class="sxs-lookup"><span data-stu-id="e97b2-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="e97b2-142">CLR は呼び出しません`Release`シャット ダウンする場合にも、ホスト管理者にします。</span><span class="sxs-lookup"><span data-stu-id="e97b2-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e97b2-143">要件</span><span class="sxs-lookup"><span data-stu-id="e97b2-143">Requirements</span></span>  
 <span data-ttu-id="e97b2-144">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e97b2-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e97b2-145">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e97b2-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e97b2-146">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e97b2-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e97b2-147">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e97b2-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e97b2-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="e97b2-148">See Also</span></span>  
 [<span data-ttu-id="e97b2-149">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e97b2-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
