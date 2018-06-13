---
title: ICLRPolicyManager::SetDefaultAction メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a183c7491ad5d67bc2c68edba3ef2d54839da12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435451"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="a9113-102">ICLRPolicyManager::SetDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="a9113-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="a9113-103">共通言語ランタイム (CLR) が、指定された操作が発生したときに実行する必要がありますポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a9113-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9113-104">構文</span><span class="sxs-lookup"><span data-stu-id="a9113-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9113-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9113-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="a9113-106">[in]1 つ、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)どの CLR の動作をカスタマイズする必要がありますアクションを示す値。</span><span class="sxs-lookup"><span data-stu-id="a9113-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="a9113-107">[in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)ポリシー アクション、CLR が実行時に示す値`operation`に発生します。</span><span class="sxs-lookup"><span data-stu-id="a9113-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9113-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a9113-108">Return Value</span></span>  
  
|<span data-ttu-id="a9113-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9113-109">HRESULT</span></span>|<span data-ttu-id="a9113-110">説明</span><span class="sxs-lookup"><span data-stu-id="a9113-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9113-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9113-111">S_OK</span></span>|<span data-ttu-id="a9113-112">`SetDefaultAction` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a9113-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="a9113-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9113-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9113-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="a9113-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9113-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9113-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9113-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a9113-116">The call timed out.</span></span>|  
|<span data-ttu-id="a9113-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9113-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9113-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a9113-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9113-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9113-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9113-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="a9113-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9113-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9113-121">E_FAIL</span></span>|<span data-ttu-id="a9113-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a9113-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9113-123">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a9113-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9113-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="a9113-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9113-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a9113-125">E_INVALIDARG</span></span>|<span data-ttu-id="a9113-126">無効な`action`が指定されました、`operation`の無効な値が指定されてまたは`operation`です。</span><span class="sxs-lookup"><span data-stu-id="a9113-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9113-127">コメント</span><span class="sxs-lookup"><span data-stu-id="a9113-127">Remarks</span></span>  
 <span data-ttu-id="a9113-128">すべてのポリシー アクションの値は、CLR 操作の既定の動作として指定できます。</span><span class="sxs-lookup"><span data-stu-id="a9113-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="a9113-129">`SetDefaultAction` 動作をエスカレートのみに通常使用できます。</span><span class="sxs-lookup"><span data-stu-id="a9113-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="a9113-130">たとえば、ホストを指定できます、スレッドの中止する rude 中止をスレッドが、その逆を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a9113-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="a9113-131">次の表は、有効な説明`action`可能性のある各値`operation`値。</span><span class="sxs-lookup"><span data-stu-id="a9113-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="a9113-132">値 `operation`</span><span class="sxs-lookup"><span data-stu-id="a9113-132">Value for `operation`</span></span>|<span data-ttu-id="a9113-133">有効な値 `action`</span><span class="sxs-lookup"><span data-stu-id="a9113-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="a9113-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="a9113-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="a9113-135">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="a9113-135">-   eAbortThread</span></span><br /><span data-ttu-id="a9113-136">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="a9113-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="a9113-137">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-138">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-139">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-139">-   eExitProcess</span></span><br /><span data-ttu-id="a9113-140">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9113-141">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9113-142">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9113-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a9113-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a9113-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="a9113-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a9113-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="a9113-145">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="a9113-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="a9113-146">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-147">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-148">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-148">-   eExitProcess</span></span><br /><span data-ttu-id="a9113-149">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9113-150">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9113-151">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9113-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a9113-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a9113-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="a9113-153">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-154">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-155">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-155">-   eExitProcess</span></span><br /><span data-ttu-id="a9113-156">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9113-157">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9113-158">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9113-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a9113-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="a9113-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="a9113-160">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-161">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-161">-   eExitProcess</span></span><br /><span data-ttu-id="a9113-162">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9113-163">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9113-164">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9113-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a9113-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a9113-165">OPR_ProcessExit</span></span>|<span data-ttu-id="a9113-166">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-166">-   eExitProcess</span></span><br /><span data-ttu-id="a9113-167">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9113-168">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9113-169">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9113-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a9113-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="a9113-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="a9113-171">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="a9113-171">-   eNoAction</span></span><br /><span data-ttu-id="a9113-172">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="a9113-172">-   eAbortThread</span></span><br /><span data-ttu-id="a9113-173">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="a9113-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="a9113-174">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-175">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a9113-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a9113-176">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-176">-   eExitProcess</span></span><br /><span data-ttu-id="a9113-177">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="a9113-178">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a9113-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a9113-179">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a9113-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9113-180">要件</span><span class="sxs-lookup"><span data-stu-id="a9113-180">Requirements</span></span>  
 <span data-ttu-id="a9113-181">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9113-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9113-182">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9113-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9113-183">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9113-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9113-184">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9113-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9113-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9113-185">See Also</span></span>  
 [<span data-ttu-id="a9113-186">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="a9113-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="a9113-187">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="a9113-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="a9113-188">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9113-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
