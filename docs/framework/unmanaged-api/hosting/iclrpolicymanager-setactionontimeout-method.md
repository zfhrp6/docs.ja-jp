---
title: "ICLRPolicyManager::SetActionOnTimeout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db0918272a315e78191624cbe6420863285620c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="a0da4-102">ICLRPolicyManager::SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="a0da4-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="a0da4-103">指定された操作がタイムアウトしたときに、共通言語ランタイム (CLR) で実行する必要がありますポリシー操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0da4-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0da4-104">構文</span><span class="sxs-lookup"><span data-stu-id="a0da4-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0da4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0da4-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="a0da4-106">[in]1 つ、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)タイムアウト アクションを指定するための操作を示す値。</span><span class="sxs-lookup"><span data-stu-id="a0da4-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="a0da4-107">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a0da4-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="a0da4-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a0da4-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="a0da4-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a0da4-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="a0da4-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a0da4-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="a0da4-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a0da4-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="a0da4-112">[in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)操作がタイムアウトになるときに実行されるポリシーのアクションを示す値。</span><span class="sxs-lookup"><span data-stu-id="a0da4-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0da4-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0da4-113">Return Value</span></span>  
  
|<span data-ttu-id="a0da4-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0da4-114">HRESULT</span></span>|<span data-ttu-id="a0da4-115">説明</span><span class="sxs-lookup"><span data-stu-id="a0da4-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0da4-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0da4-116">S_OK</span></span>|<span data-ttu-id="a0da4-117">`SetActionOnTimeout`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a0da4-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="a0da4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0da4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0da4-119">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="a0da4-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0da4-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0da4-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0da4-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a0da4-121">The call timed out.</span></span>|  
|<span data-ttu-id="a0da4-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0da4-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0da4-123">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a0da4-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0da4-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0da4-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0da4-125">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="a0da4-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0da4-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0da4-126">E_FAIL</span></span>|<span data-ttu-id="a0da4-127">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a0da4-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0da4-128">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a0da4-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0da4-129">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="a0da4-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a0da4-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a0da4-130">E_INVALIDARG</span></span>|<span data-ttu-id="a0da4-131">タイムアウトを設定することはできません、指定された`operation`の無効な値が指定されてまたは`operation`です。</span><span class="sxs-lookup"><span data-stu-id="a0da4-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0da4-132">コメント</span><span class="sxs-lookup"><span data-stu-id="a0da4-132">Remarks</span></span>  
 <span data-ttu-id="a0da4-133">タイムアウト値は、CLR によって設定されている既定のタイムアウトまたはへの呼び出しにホストによって指定された値のいずれかを指定できます、 [iclrpolicymanager::settimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a0da4-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="a0da4-134">すべてのポリシー アクションの値は、CLR 操作のタイムアウトの動作として指定できます。</span><span class="sxs-lookup"><span data-stu-id="a0da4-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="a0da4-135">`SetActionOnTimeout`通常の動作を報告するのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0da4-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="a0da4-136">たとえば、ホストを指定できます、スレッドの中止する rude 中止をスレッドが、その逆を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a0da4-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="a0da4-137">次の表は、有効な説明`action`の値が有効な`operation`値。</span><span class="sxs-lookup"><span data-stu-id="a0da4-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="a0da4-138">値`operation`</span><span class="sxs-lookup"><span data-stu-id="a0da4-138">Value for `operation`</span></span>|<span data-ttu-id="a0da4-139">有効な値`action`</span><span class="sxs-lookup"><span data-stu-id="a0da4-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="a0da4-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a0da4-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="a0da4-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a0da4-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="a0da4-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="a0da4-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="a0da4-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a0da4-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a0da4-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a0da4-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a0da4-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-145">-   eExitProcess</span></span><br /><span data-ttu-id="a0da4-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="a0da4-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a0da4-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a0da4-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a0da4-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a0da4-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="a0da4-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a0da4-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a0da4-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a0da4-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a0da4-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-152">-   eExitProcess</span></span><br /><span data-ttu-id="a0da4-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="a0da4-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a0da4-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a0da4-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a0da4-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a0da4-156">OPR_ProcessExit</span></span>|<span data-ttu-id="a0da4-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-157">-   eExitProcess</span></span><br /><span data-ttu-id="a0da4-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="a0da4-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a0da4-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a0da4-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a0da4-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0da4-161">必要条件</span><span class="sxs-lookup"><span data-stu-id="a0da4-161">Requirements</span></span>  
 <span data-ttu-id="a0da4-162">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0da4-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0da4-163">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a0da4-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0da4-164">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0da4-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0da4-165">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0da4-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0da4-166">参照</span><span class="sxs-lookup"><span data-stu-id="a0da4-166">See Also</span></span>  
 [<span data-ttu-id="a0da4-167">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="a0da4-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="a0da4-168">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="a0da4-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="a0da4-169">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0da4-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a0da4-170">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0da4-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
