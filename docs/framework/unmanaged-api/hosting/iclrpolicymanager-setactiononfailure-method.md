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
ms.openlocfilehash: 5dc8e27ed1a5701886c3583a7515e4212f490208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="b1ac6-102">ICLRPolicyManager::SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="b1ac6-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="b1ac6-103">指定したエラーが発生したときに、共通言語ランタイム (CLR) が実行するポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ac6-104">構文</span><span class="sxs-lookup"><span data-stu-id="b1ac6-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1ac6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b1ac6-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="b1ac6-106">[in]1 つ、 [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)アクションを実行する対象のエラーの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="b1ac6-107">[in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)障害が発生したときに実行されるアクションを示す値。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="b1ac6-108">サポートされている値の一覧は、「解説」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1ac6-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="b1ac6-109">Return Value</span></span>  
  
|<span data-ttu-id="b1ac6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1ac6-110">HRESULT</span></span>|<span data-ttu-id="b1ac6-111">説明</span><span class="sxs-lookup"><span data-stu-id="b1ac6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1ac6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1ac6-112">S_OK</span></span>|<span data-ttu-id="b1ac6-113">`SetActionOnFailure`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="b1ac6-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1ac6-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1ac6-115">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1ac6-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1ac6-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1ac6-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-117">The call timed out.</span></span>|  
|<span data-ttu-id="b1ac6-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1ac6-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1ac6-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1ac6-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1ac6-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1ac6-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1ac6-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1ac6-122">E_FAIL</span></span>|<span data-ttu-id="b1ac6-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1ac6-124">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1ac6-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1ac6-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b1ac6-126">E_INVALIDARG</span></span>|<span data-ttu-id="b1ac6-127">指定された操作のポリシーのアクションを設定することはできませんか、操作の無効なポリシー アクションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1ac6-128">コメント</span><span class="sxs-lookup"><span data-stu-id="b1ac6-128">Remarks</span></span>  
 <span data-ttu-id="b1ac6-129">既定では、メモリなどのリソースの割り当てに失敗した場合、CLR は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="b1ac6-130">`SetActionOnFailure`エラー発生時に実行するポリシーのアクションを指定することによってこの動作をオーバーライドをホストできるようにします。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="b1ac6-131">次の表は、組み合わせの[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)と[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)サポートされている値。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="b1ac6-132">(から FAIL_ プレフィックスを省略すると[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)値です)。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="b1ac6-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="b1ac6-133">NonCriticalResource</span></span>|<span data-ttu-id="b1ac6-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="b1ac6-134">CriticalResource</span></span>|<span data-ttu-id="b1ac6-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="b1ac6-135">FatalRuntime</span></span>|<span data-ttu-id="b1ac6-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="b1ac6-136">OrphanedLock</span></span>|<span data-ttu-id="b1ac6-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="b1ac6-137">StackOverflow</span></span>|<span data-ttu-id="b1ac6-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="b1ac6-138">AccessViolation</span></span>|<span data-ttu-id="b1ac6-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="b1ac6-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="b1ac6-140">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-140">X</span></span>|<span data-ttu-id="b1ac6-141">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-141">X</span></span>||||<span data-ttu-id="b1ac6-142">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-142">N/A</span></span>||  
|<span data-ttu-id="b1ac6-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="b1ac6-143">eThrowException</span></span>|<span data-ttu-id="b1ac6-144">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-144">X</span></span>|<span data-ttu-id="b1ac6-145">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-145">X</span></span>||||<span data-ttu-id="b1ac6-146">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="b1ac6-147">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-147">X</span></span>|<span data-ttu-id="b1ac6-148">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-148">X</span></span>||||<span data-ttu-id="b1ac6-149">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-149">N/A</span></span>|<span data-ttu-id="b1ac6-150">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="b1ac6-151">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-151">X</span></span>|<span data-ttu-id="b1ac6-152">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-152">X</span></span>||||<span data-ttu-id="b1ac6-153">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-153">N/A</span></span>|<span data-ttu-id="b1ac6-154">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="b1ac6-155">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-155">X</span></span>|<span data-ttu-id="b1ac6-156">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-156">X</span></span>||<span data-ttu-id="b1ac6-157">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-157">X</span></span>||<span data-ttu-id="b1ac6-158">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-158">N/A</span></span>|<span data-ttu-id="b1ac6-159">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="b1ac6-160">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-160">X</span></span>|<span data-ttu-id="b1ac6-161">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-161">X</span></span>||<span data-ttu-id="b1ac6-162">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-162">X</span></span>|<span data-ttu-id="b1ac6-163">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-163">X</span></span>|<span data-ttu-id="b1ac6-164">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-164">N/A</span></span>|<span data-ttu-id="b1ac6-165">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="b1ac6-166">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-166">X</span></span>|<span data-ttu-id="b1ac6-167">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-167">X</span></span>||<span data-ttu-id="b1ac6-168">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-168">X</span></span>|<span data-ttu-id="b1ac6-169">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-169">X</span></span>|<span data-ttu-id="b1ac6-170">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-170">N/A</span></span>|<span data-ttu-id="b1ac6-171">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-171">X</span></span>|  
|<span data-ttu-id="b1ac6-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="b1ac6-172">eFastExitProcess</span></span>|<span data-ttu-id="b1ac6-173">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-173">X</span></span>|<span data-ttu-id="b1ac6-174">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-174">X</span></span>||<span data-ttu-id="b1ac6-175">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-175">X</span></span>|<span data-ttu-id="b1ac6-176">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-176">X</span></span>|<span data-ttu-id="b1ac6-177">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="b1ac6-178">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-178">X</span></span>|<span data-ttu-id="b1ac6-179">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-179">X</span></span>|<span data-ttu-id="b1ac6-180">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-180">X</span></span>|<span data-ttu-id="b1ac6-181">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-181">X</span></span>|<span data-ttu-id="b1ac6-182">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-182">X</span></span>|<span data-ttu-id="b1ac6-183">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="b1ac6-184">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-184">X</span></span>|<span data-ttu-id="b1ac6-185">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-185">X</span></span>|<span data-ttu-id="b1ac6-186">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-186">X</span></span>|<span data-ttu-id="b1ac6-187">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-187">X</span></span>|<span data-ttu-id="b1ac6-188">X</span><span class="sxs-lookup"><span data-stu-id="b1ac6-188">X</span></span>|<span data-ttu-id="b1ac6-189">N/A</span><span class="sxs-lookup"><span data-stu-id="b1ac6-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="b1ac6-190">要件</span><span class="sxs-lookup"><span data-stu-id="b1ac6-190">Requirements</span></span>  
 <span data-ttu-id="b1ac6-191">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1ac6-192">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1ac6-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1ac6-193">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1ac6-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1ac6-194">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1ac6-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ac6-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1ac6-195">See Also</span></span>  
 [<span data-ttu-id="b1ac6-196">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="b1ac6-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="b1ac6-197">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="b1ac6-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="b1ac6-198">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1ac6-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b1ac6-199">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1ac6-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
