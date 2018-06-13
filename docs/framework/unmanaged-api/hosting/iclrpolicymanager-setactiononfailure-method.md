---
title: ICLRPolicyManager::SetActionOnFailure メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc3616b2cec0fa951df745e3c5f0468f74ab82bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435930"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="78bd9-102">ICLRPolicyManager::SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="78bd9-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="78bd9-103">指定したエラーが発生したときに、共通言語ランタイム (CLR) が実行するポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="78bd9-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bd9-104">構文</span><span class="sxs-lookup"><span data-stu-id="78bd9-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78bd9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78bd9-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="78bd9-106">[in]1 つ、 [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)アクションを実行する対象のエラーの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="78bd9-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="78bd9-107">[in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)障害が発生したときに実行されるアクションを示す値。</span><span class="sxs-lookup"><span data-stu-id="78bd9-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="78bd9-108">サポートされている値の一覧は、「解説」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78bd9-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78bd9-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="78bd9-109">Return Value</span></span>  
  
|<span data-ttu-id="78bd9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78bd9-110">HRESULT</span></span>|<span data-ttu-id="78bd9-111">説明</span><span class="sxs-lookup"><span data-stu-id="78bd9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78bd9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="78bd9-112">S_OK</span></span>|<span data-ttu-id="78bd9-113">`SetActionOnFailure` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="78bd9-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="78bd9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78bd9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78bd9-115">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="78bd9-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78bd9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78bd9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78bd9-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="78bd9-117">The call timed out.</span></span>|  
|<span data-ttu-id="78bd9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78bd9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78bd9-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="78bd9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78bd9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78bd9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78bd9-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="78bd9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78bd9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78bd9-122">E_FAIL</span></span>|<span data-ttu-id="78bd9-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="78bd9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78bd9-124">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="78bd9-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78bd9-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="78bd9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="78bd9-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="78bd9-126">E_INVALIDARG</span></span>|<span data-ttu-id="78bd9-127">指定された操作のポリシーのアクションを設定することはできませんか、操作の無効なポリシー アクションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="78bd9-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78bd9-128">コメント</span><span class="sxs-lookup"><span data-stu-id="78bd9-128">Remarks</span></span>  
 <span data-ttu-id="78bd9-129">既定では、メモリなどのリソースの割り当てに失敗した場合、CLR は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="78bd9-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="78bd9-130">`SetActionOnFailure` エラー発生時に実行するポリシーのアクションを指定することによってこの動作をオーバーライドをホストできるようにします。</span><span class="sxs-lookup"><span data-stu-id="78bd9-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="78bd9-131">次の表は、組み合わせの[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)と[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)サポートされている値。</span><span class="sxs-lookup"><span data-stu-id="78bd9-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="78bd9-132">(から FAIL_ プレフィックスを省略すると[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)値です)。</span><span class="sxs-lookup"><span data-stu-id="78bd9-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="78bd9-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="78bd9-133">NonCriticalResource</span></span>|<span data-ttu-id="78bd9-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="78bd9-134">CriticalResource</span></span>|<span data-ttu-id="78bd9-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="78bd9-135">FatalRuntime</span></span>|<span data-ttu-id="78bd9-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="78bd9-136">OrphanedLock</span></span>|<span data-ttu-id="78bd9-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="78bd9-137">StackOverflow</span></span>|<span data-ttu-id="78bd9-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="78bd9-138">AccessViolation</span></span>|<span data-ttu-id="78bd9-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="78bd9-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="78bd9-140">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-140">X</span></span>|<span data-ttu-id="78bd9-141">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-141">X</span></span>||||<span data-ttu-id="78bd9-142">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-142">N/A</span></span>||  
|<span data-ttu-id="78bd9-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="78bd9-143">eThrowException</span></span>|<span data-ttu-id="78bd9-144">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-144">X</span></span>|<span data-ttu-id="78bd9-145">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-145">X</span></span>||||<span data-ttu-id="78bd9-146">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="78bd9-147">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-147">X</span></span>|<span data-ttu-id="78bd9-148">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-148">X</span></span>||||<span data-ttu-id="78bd9-149">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-149">N/A</span></span>|<span data-ttu-id="78bd9-150">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="78bd9-151">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-151">X</span></span>|<span data-ttu-id="78bd9-152">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-152">X</span></span>||||<span data-ttu-id="78bd9-153">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-153">N/A</span></span>|<span data-ttu-id="78bd9-154">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="78bd9-155">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-155">X</span></span>|<span data-ttu-id="78bd9-156">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-156">X</span></span>||<span data-ttu-id="78bd9-157">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-157">X</span></span>||<span data-ttu-id="78bd9-158">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-158">N/A</span></span>|<span data-ttu-id="78bd9-159">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="78bd9-160">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-160">X</span></span>|<span data-ttu-id="78bd9-161">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-161">X</span></span>||<span data-ttu-id="78bd9-162">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-162">X</span></span>|<span data-ttu-id="78bd9-163">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-163">X</span></span>|<span data-ttu-id="78bd9-164">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-164">N/A</span></span>|<span data-ttu-id="78bd9-165">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="78bd9-166">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-166">X</span></span>|<span data-ttu-id="78bd9-167">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-167">X</span></span>||<span data-ttu-id="78bd9-168">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-168">X</span></span>|<span data-ttu-id="78bd9-169">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-169">X</span></span>|<span data-ttu-id="78bd9-170">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-170">N/A</span></span>|<span data-ttu-id="78bd9-171">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-171">X</span></span>|  
|<span data-ttu-id="78bd9-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="78bd9-172">eFastExitProcess</span></span>|<span data-ttu-id="78bd9-173">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-173">X</span></span>|<span data-ttu-id="78bd9-174">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-174">X</span></span>||<span data-ttu-id="78bd9-175">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-175">X</span></span>|<span data-ttu-id="78bd9-176">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-176">X</span></span>|<span data-ttu-id="78bd9-177">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="78bd9-178">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-178">X</span></span>|<span data-ttu-id="78bd9-179">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-179">X</span></span>|<span data-ttu-id="78bd9-180">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-180">X</span></span>|<span data-ttu-id="78bd9-181">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-181">X</span></span>|<span data-ttu-id="78bd9-182">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-182">X</span></span>|<span data-ttu-id="78bd9-183">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="78bd9-184">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-184">X</span></span>|<span data-ttu-id="78bd9-185">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-185">X</span></span>|<span data-ttu-id="78bd9-186">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-186">X</span></span>|<span data-ttu-id="78bd9-187">X</span><span class="sxs-lookup"><span data-stu-id="78bd9-187">X</span></span>|<span data-ttu-id="78bd9-188">x</span><span class="sxs-lookup"><span data-stu-id="78bd9-188">X</span></span>|<span data-ttu-id="78bd9-189">N/A</span><span class="sxs-lookup"><span data-stu-id="78bd9-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="78bd9-190">要件</span><span class="sxs-lookup"><span data-stu-id="78bd9-190">Requirements</span></span>  
 <span data-ttu-id="78bd9-191">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78bd9-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78bd9-192">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78bd9-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78bd9-193">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="78bd9-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78bd9-194">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78bd9-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78bd9-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="78bd9-195">See Also</span></span>  
 [<span data-ttu-id="78bd9-196">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="78bd9-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="78bd9-197">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="78bd9-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="78bd9-198">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78bd9-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="78bd9-199">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78bd9-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
