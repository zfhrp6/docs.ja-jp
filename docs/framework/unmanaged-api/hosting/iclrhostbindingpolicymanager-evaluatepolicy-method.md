---
title: ICLRHostBindingPolicyManager::EvaluatePolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e37d56a321e6529812045e37c4f1929818b38a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433608"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="568f6-102">ICLRHostBindingPolicyManager::EvaluatePolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="568f6-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="568f6-103">ホストの代わりには、バインディング ポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="568f6-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="568f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="568f6-104">Syntax</span></span>  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="568f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="568f6-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="568f6-106">[in]ポリシーの評価する前にアセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="568f6-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="568f6-107">[in]ポリシー データを格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="568f6-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="568f6-108">[in]サイズ、`pbApplicationPolicy`バッファー。</span><span class="sxs-lookup"><span data-stu-id="568f6-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="568f6-109">[out]新しいポリシー データの評価後に、アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="568f6-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="568f6-110">[入力、出力].バッファーのサイズ、アセンブリの id 参照、新しいポリシー データの評価の後へのポインター。</span><span class="sxs-lookup"><span data-stu-id="568f6-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="568f6-111">[out]論理 OR の組み合わせへのポインター [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md)されるポリシーが適用されていることを示す値。</span><span class="sxs-lookup"><span data-stu-id="568f6-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="568f6-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="568f6-112">Return Value</span></span>  
  
|<span data-ttu-id="568f6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="568f6-113">HRESULT</span></span>|<span data-ttu-id="568f6-114">説明</span><span class="sxs-lookup"><span data-stu-id="568f6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="568f6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="568f6-115">S_OK</span></span>|<span data-ttu-id="568f6-116">正常に完了した評価します。</span><span class="sxs-lookup"><span data-stu-id="568f6-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="568f6-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="568f6-117">E_INVALIDARG</span></span>|<span data-ttu-id="568f6-118">いずれか`pwzReferenceIdentity`または`pbApplicationPolicy`null 参照です。</span><span class="sxs-lookup"><span data-stu-id="568f6-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="568f6-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="568f6-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="568f6-120">`cbAppPolicySize` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="568f6-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="568f6-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="568f6-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="568f6-122">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="568f6-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="568f6-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="568f6-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="568f6-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="568f6-124">The call timed out.</span></span>|  
|<span data-ttu-id="568f6-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="568f6-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="568f6-126">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="568f6-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="568f6-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="568f6-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="568f6-128">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="568f6-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="568f6-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="568f6-129">E_FAIL</span></span>|<span data-ttu-id="568f6-130">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="568f6-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="568f6-131">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="568f6-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="568f6-132">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="568f6-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="568f6-133">コメント</span><span class="sxs-lookup"><span data-stu-id="568f6-133">Remarks</span></span>  
 <span data-ttu-id="568f6-134">`EvaluatePolicy`メソッドによりバージョン管理の要件、ホスト固有のアセンブリを維持するためにバインディング ポリシーをホストします。</span><span class="sxs-lookup"><span data-stu-id="568f6-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="568f6-135">自体ポリシー エンジンは、CLR 内に残ります。</span><span class="sxs-lookup"><span data-stu-id="568f6-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="568f6-136">要件</span><span class="sxs-lookup"><span data-stu-id="568f6-136">Requirements</span></span>  
 <span data-ttu-id="568f6-137">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="568f6-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="568f6-138">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="568f6-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="568f6-139">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="568f6-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="568f6-140">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="568f6-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568f6-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="568f6-141">See Also</span></span>  
 [<span data-ttu-id="568f6-142">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="568f6-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
