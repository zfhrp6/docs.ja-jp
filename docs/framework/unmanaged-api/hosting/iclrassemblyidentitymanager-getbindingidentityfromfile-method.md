---
title: "ICLRAssemblyIdentityManager::GetBindingIdentityFromFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 140240f5f108cdd26cd0e813d7fe47f102a3b941
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="71567-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="71567-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="71567-103">指定したファイル パスにあるアセンブリのデータのバインドのアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="71567-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71567-104">構文</span><span class="sxs-lookup"><span data-stu-id="71567-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71567-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71567-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="71567-106">[in]評価するファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="71567-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="71567-107">[in]値、 [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md)をアセンブリの id の種類を示す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="71567-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="71567-108">将来の機能拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="71567-108">Provided for future extensibility.</span></span> <span data-ttu-id="71567-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) 2.0 をサポートする唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="71567-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="71567-110">[out]不透明なアセンブリの id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="71567-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="71567-111">[入力、出力].サイズへのポインター`pwzBuffer`です。</span><span class="sxs-lookup"><span data-stu-id="71567-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71567-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="71567-112">Return Value</span></span>  
  
|<span data-ttu-id="71567-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71567-113">HRESULT</span></span>|<span data-ttu-id="71567-114">説明</span><span class="sxs-lookup"><span data-stu-id="71567-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71567-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="71567-115">S_OK</span></span>|<span data-ttu-id="71567-116">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="71567-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="71567-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="71567-117">E_INVALIDARG</span></span>|<span data-ttu-id="71567-118">指定された`pwzFilePath`が null です。</span><span class="sxs-lookup"><span data-stu-id="71567-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="71567-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="71567-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="71567-120">サイズ`pwzBuffer`が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="71567-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="71567-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71567-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71567-122">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="71567-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71567-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71567-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71567-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="71567-124">The call timed out.</span></span>|  
|<span data-ttu-id="71567-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71567-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71567-126">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="71567-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71567-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71567-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71567-128">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="71567-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71567-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71567-129">E_FAIL</span></span>|<span data-ttu-id="71567-130">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="71567-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71567-131">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="71567-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71567-132">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="71567-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71567-133">コメント</span><span class="sxs-lookup"><span data-stu-id="71567-133">Remarks</span></span>  
 <span data-ttu-id="71567-134">`GetBindingIdentityFromFile`通常 2 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="71567-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="71567-135">最初の呼び出しに対して null 値を提供する`pwzBuffer`、適切なサイズが返されます`pcchBufferSize`です。</span><span class="sxs-lookup"><span data-stu-id="71567-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="71567-136">2 番目の呼び出しが適切に割り当てられたバッファーを提供し、メソッドが完了したときに実際のバッファーのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="71567-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71567-137">要件</span><span class="sxs-lookup"><span data-stu-id="71567-137">Requirements</span></span>  
 <span data-ttu-id="71567-138">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="71567-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71567-139">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71567-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71567-140">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="71567-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71567-141">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71567-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71567-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="71567-142">See Also</span></span>  
 [<span data-ttu-id="71567-143">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71567-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="71567-144">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71567-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="71567-145">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71567-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
