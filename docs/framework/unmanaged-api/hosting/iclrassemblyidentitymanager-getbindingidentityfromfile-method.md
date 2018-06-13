---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28e97289eda5949e6d124426eb58105e2e3ad33e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435043"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="84f21-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="84f21-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="84f21-103">指定したファイル パスにあるアセンブリのデータのバインドのアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="84f21-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f21-104">構文</span><span class="sxs-lookup"><span data-stu-id="84f21-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84f21-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="84f21-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="84f21-106">[in]評価するファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="84f21-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="84f21-107">[in]値、 [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md)をアセンブリの id の種類を示す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="84f21-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="84f21-108">将来の機能拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="84f21-108">Provided for future extensibility.</span></span> <span data-ttu-id="84f21-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) 2.0 をサポートする唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="84f21-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="84f21-110">[out]不透明なアセンブリの id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="84f21-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="84f21-111">[入力、出力].サイズへのポインター`pwzBuffer`です。</span><span class="sxs-lookup"><span data-stu-id="84f21-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84f21-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="84f21-112">Return Value</span></span>  
  
|<span data-ttu-id="84f21-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84f21-113">HRESULT</span></span>|<span data-ttu-id="84f21-114">説明</span><span class="sxs-lookup"><span data-stu-id="84f21-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84f21-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="84f21-115">S_OK</span></span>|<span data-ttu-id="84f21-116">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="84f21-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="84f21-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="84f21-117">E_INVALIDARG</span></span>|<span data-ttu-id="84f21-118">指定された`pwzFilePath`が null です。</span><span class="sxs-lookup"><span data-stu-id="84f21-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="84f21-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="84f21-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="84f21-120">サイズ`pwzBuffer`が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="84f21-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="84f21-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="84f21-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="84f21-122">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="84f21-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="84f21-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="84f21-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="84f21-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="84f21-124">The call timed out.</span></span>|  
|<span data-ttu-id="84f21-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="84f21-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="84f21-126">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="84f21-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="84f21-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="84f21-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="84f21-128">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="84f21-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="84f21-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="84f21-129">E_FAIL</span></span>|<span data-ttu-id="84f21-130">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="84f21-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="84f21-131">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="84f21-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="84f21-132">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="84f21-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84f21-133">コメント</span><span class="sxs-lookup"><span data-stu-id="84f21-133">Remarks</span></span>  
 <span data-ttu-id="84f21-134">`GetBindingIdentityFromFile` 通常 2 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="84f21-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="84f21-135">最初の呼び出しに対して null 値を提供する`pwzBuffer`、適切なサイズが返されます`pcchBufferSize`です。</span><span class="sxs-lookup"><span data-stu-id="84f21-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="84f21-136">2 番目の呼び出しが適切に割り当てられたバッファーを提供し、メソッドが完了したときに実際のバッファーのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="84f21-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84f21-137">要件</span><span class="sxs-lookup"><span data-stu-id="84f21-137">Requirements</span></span>  
 <span data-ttu-id="84f21-138">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="84f21-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84f21-139">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="84f21-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84f21-140">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="84f21-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84f21-141">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84f21-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f21-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="84f21-142">See Also</span></span>  
 [<span data-ttu-id="84f21-143">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84f21-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="84f21-144">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84f21-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="84f21-145">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84f21-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
