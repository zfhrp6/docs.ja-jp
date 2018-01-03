---
title: "ICLRPolicyManager::SetActionOnFailure メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4440b36485ed900b5e64adcead2525dbb7d5206e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="11dbc-102">ICLRPolicyManager::SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="11dbc-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="11dbc-103">指定したエラーが発生したときに、共通言語ランタイム (CLR) が実行するポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="11dbc-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11dbc-104">構文</span><span class="sxs-lookup"><span data-stu-id="11dbc-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11dbc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11dbc-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="11dbc-106">[in]1 つ、 [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)アクションを実行する対象のエラーの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="11dbc-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="11dbc-107">[in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)障害が発生したときに実行されるアクションを示す値。</span><span class="sxs-lookup"><span data-stu-id="11dbc-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="11dbc-108">サポートされている値の一覧は、「解説」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="11dbc-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11dbc-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="11dbc-109">Return Value</span></span>  
  
|<span data-ttu-id="11dbc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11dbc-110">HRESULT</span></span>|<span data-ttu-id="11dbc-111">説明</span><span class="sxs-lookup"><span data-stu-id="11dbc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11dbc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="11dbc-112">S_OK</span></span>|<span data-ttu-id="11dbc-113">`SetActionOnFailure`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="11dbc-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="11dbc-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11dbc-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11dbc-115">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="11dbc-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11dbc-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11dbc-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11dbc-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="11dbc-117">The call timed out.</span></span>|  
|<span data-ttu-id="11dbc-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11dbc-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11dbc-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="11dbc-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11dbc-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11dbc-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11dbc-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="11dbc-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11dbc-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11dbc-122">E_FAIL</span></span>|<span data-ttu-id="11dbc-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="11dbc-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11dbc-124">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="11dbc-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11dbc-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="11dbc-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11dbc-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="11dbc-126">E_INVALIDARG</span></span>|<span data-ttu-id="11dbc-127">指定された操作のポリシーのアクションを設定することはできませんか、操作の無効なポリシー アクションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="11dbc-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11dbc-128">コメント</span><span class="sxs-lookup"><span data-stu-id="11dbc-128">Remarks</span></span>  
 <span data-ttu-id="11dbc-129">既定では、メモリなどのリソースの割り当てに失敗した場合、CLR は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="11dbc-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="11dbc-130">`SetActionOnFailure`エラー発生時に実行するポリシーのアクションを指定することによってこの動作をオーバーライドをホストできるようにします。</span><span class="sxs-lookup"><span data-stu-id="11dbc-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="11dbc-131">次の表は、組み合わせの[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)と[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)サポートされている値。</span><span class="sxs-lookup"><span data-stu-id="11dbc-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="11dbc-132">(から FAIL_ プレフィックスを省略すると[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)値です)。</span><span class="sxs-lookup"><span data-stu-id="11dbc-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="11dbc-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="11dbc-133">NonCriticalResource</span></span>|<span data-ttu-id="11dbc-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="11dbc-134">CriticalResource</span></span>|<span data-ttu-id="11dbc-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="11dbc-135">FatalRuntime</span></span>|<span data-ttu-id="11dbc-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="11dbc-136">OrphanedLock</span></span>|<span data-ttu-id="11dbc-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="11dbc-137">StackOverflow</span></span>|<span data-ttu-id="11dbc-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="11dbc-138">AccessViolation</span></span>|<span data-ttu-id="11dbc-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="11dbc-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="11dbc-140">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-140">X</span></span>|<span data-ttu-id="11dbc-141">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-141">X</span></span>||||<span data-ttu-id="11dbc-142">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-142">N/A</span></span>||  
|<span data-ttu-id="11dbc-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="11dbc-143">eThrowException</span></span>|<span data-ttu-id="11dbc-144">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-144">X</span></span>|<span data-ttu-id="11dbc-145">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-145">X</span></span>||||<span data-ttu-id="11dbc-146">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="11dbc-147">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-147">X</span></span>|<span data-ttu-id="11dbc-148">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-148">X</span></span>||||<span data-ttu-id="11dbc-149">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-149">N/A</span></span>|<span data-ttu-id="11dbc-150">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="11dbc-151">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-151">X</span></span>|<span data-ttu-id="11dbc-152">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-152">X</span></span>||||<span data-ttu-id="11dbc-153">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-153">N/A</span></span>|<span data-ttu-id="11dbc-154">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="11dbc-155">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-155">X</span></span>|<span data-ttu-id="11dbc-156">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-156">X</span></span>||<span data-ttu-id="11dbc-157">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-157">X</span></span>||<span data-ttu-id="11dbc-158">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-158">N/A</span></span>|<span data-ttu-id="11dbc-159">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="11dbc-160">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-160">X</span></span>|<span data-ttu-id="11dbc-161">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-161">X</span></span>||<span data-ttu-id="11dbc-162">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-162">X</span></span>|<span data-ttu-id="11dbc-163">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-163">X</span></span>|<span data-ttu-id="11dbc-164">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-164">N/A</span></span>|<span data-ttu-id="11dbc-165">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="11dbc-166">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-166">X</span></span>|<span data-ttu-id="11dbc-167">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-167">X</span></span>||<span data-ttu-id="11dbc-168">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-168">X</span></span>|<span data-ttu-id="11dbc-169">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-169">X</span></span>|<span data-ttu-id="11dbc-170">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-170">N/A</span></span>|<span data-ttu-id="11dbc-171">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-171">X</span></span>|  
|<span data-ttu-id="11dbc-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="11dbc-172">eFastExitProcess</span></span>|<span data-ttu-id="11dbc-173">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-173">X</span></span>|<span data-ttu-id="11dbc-174">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-174">X</span></span>||<span data-ttu-id="11dbc-175">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-175">X</span></span>|<span data-ttu-id="11dbc-176">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-176">X</span></span>|<span data-ttu-id="11dbc-177">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="11dbc-178">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-178">X</span></span>|<span data-ttu-id="11dbc-179">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-179">X</span></span>|<span data-ttu-id="11dbc-180">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-180">X</span></span>|<span data-ttu-id="11dbc-181">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-181">X</span></span>|<span data-ttu-id="11dbc-182">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-182">X</span></span>|<span data-ttu-id="11dbc-183">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="11dbc-184">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-184">X</span></span>|<span data-ttu-id="11dbc-185">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-185">X</span></span>|<span data-ttu-id="11dbc-186">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-186">X</span></span>|<span data-ttu-id="11dbc-187">X</span><span class="sxs-lookup"><span data-stu-id="11dbc-187">X</span></span>|<span data-ttu-id="11dbc-188">x</span><span class="sxs-lookup"><span data-stu-id="11dbc-188">X</span></span>|<span data-ttu-id="11dbc-189">N/A</span><span class="sxs-lookup"><span data-stu-id="11dbc-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="11dbc-190">必要条件</span><span class="sxs-lookup"><span data-stu-id="11dbc-190">Requirements</span></span>  
 <span data-ttu-id="11dbc-191">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="11dbc-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11dbc-192">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11dbc-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11dbc-193">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="11dbc-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11dbc-194">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11dbc-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11dbc-195">参照</span><span class="sxs-lookup"><span data-stu-id="11dbc-195">See Also</span></span>  
 [<span data-ttu-id="11dbc-196">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="11dbc-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="11dbc-197">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="11dbc-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="11dbc-198">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11dbc-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="11dbc-199">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11dbc-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
