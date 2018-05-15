---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a221b286ada97c3c03387556cb30ee6ddd2c453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="20abf-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="20abf-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="20abf-103">指定したアセンブリのバインディング ポリシーを変更し、新しいバージョンのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="20abf-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20abf-104">構文</span><span class="sxs-lookup"><span data-stu-id="20abf-104">Syntax</span></span>  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20abf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20abf-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="20abf-106">[in]変更するアセンブリの id。</span><span class="sxs-lookup"><span data-stu-id="20abf-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="20abf-107">[in]変更後のアセンブリの新しい id。</span><span class="sxs-lookup"><span data-stu-id="20abf-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="20abf-108">[in]変更するアセンブリのバインディング ポリシー データを格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="20abf-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="20abf-109">[in]置き換えられるバインディング ポリシーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="20abf-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="20abf-110">[in]論理 OR の組み合わせの[EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)リダイレクトのコントロールを示す値。</span><span class="sxs-lookup"><span data-stu-id="20abf-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="20abf-111">[out]新しいデータのバインディング ポリシーを格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="20abf-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="20abf-112">[入力、出力].新しいバインド ポリシー バッファーのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="20abf-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20abf-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="20abf-113">Return Value</span></span>  
  
|<span data-ttu-id="20abf-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20abf-114">HRESULT</span></span>|<span data-ttu-id="20abf-115">説明</span><span class="sxs-lookup"><span data-stu-id="20abf-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20abf-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="20abf-116">S_OK</span></span>|<span data-ttu-id="20abf-117">ポリシーは正常に変更されました。</span><span class="sxs-lookup"><span data-stu-id="20abf-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="20abf-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="20abf-118">E_INVALIDARG</span></span>|<span data-ttu-id="20abf-119">`pwzSourceAssemblyIdentity` または`pwzTargetAssemblyIdentity`が null 参照でした。</span><span class="sxs-lookup"><span data-stu-id="20abf-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="20abf-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="20abf-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="20abf-121">`pbNewApplicationPolicy` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="20abf-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="20abf-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20abf-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20abf-123">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="20abf-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20abf-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20abf-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20abf-125">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="20abf-125">The call timed out.</span></span>|  
|<span data-ttu-id="20abf-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20abf-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20abf-127">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="20abf-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20abf-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20abf-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20abf-129">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="20abf-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20abf-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20abf-130">E_FAIL</span></span>|<span data-ttu-id="20abf-131">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="20abf-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20abf-132">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="20abf-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20abf-133">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="20abf-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20abf-134">コメント</span><span class="sxs-lookup"><span data-stu-id="20abf-134">Remarks</span></span>  
 <span data-ttu-id="20abf-135">`ModifyApplicationPolicy`メソッドを 2 回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="20abf-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="20abf-136">最初の呼び出しは、null 値を指定する必要があります、`pbNewApplicationPolicy`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="20abf-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="20abf-137">この呼び出しのために必要な値が返さ`pcbNewAppPolicySize`です。</span><span class="sxs-lookup"><span data-stu-id="20abf-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="20abf-138">2 つ目の呼び出しは、のこの値を指定する必要があります`pcbNewAppPolicySize`の特定のサイズのバッファーを指す`pbNewApplicationPolicy`です。</span><span class="sxs-lookup"><span data-stu-id="20abf-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20abf-139">要件</span><span class="sxs-lookup"><span data-stu-id="20abf-139">Requirements</span></span>  
 <span data-ttu-id="20abf-140">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="20abf-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20abf-141">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20abf-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20abf-142">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="20abf-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20abf-143">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20abf-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20abf-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="20abf-144">See Also</span></span>  
 [<span data-ttu-id="20abf-145">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20abf-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
