---
title: "ICLRAssemblyIdentityManager::GetBindingIdentityFromStream メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd16f13bd77127953bdd17b258c7be518088f899
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="4faab-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="4faab-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="4faab-103">指定したストリーム内のアセンブリの標準アセンブリの id データを取得します。</span><span class="sxs-lookup"><span data-stu-id="4faab-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4faab-104">構文</span><span class="sxs-lookup"><span data-stu-id="4faab-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4faab-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4faab-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="4faab-106">[in]評価するアセンブリのストリーム。</span><span class="sxs-lookup"><span data-stu-id="4faab-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4faab-107">[in]将来の機能拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="4faab-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="4faab-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンをサポートする唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="4faab-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="4faab-109">[out]不透明なアセンブリの id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="4faab-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="4faab-110">[入力、出力].サイズ`pwzBuffer`です。</span><span class="sxs-lookup"><span data-stu-id="4faab-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4faab-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="4faab-111">Return Value</span></span>  
  
|<span data-ttu-id="4faab-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4faab-112">HRESULT</span></span>|<span data-ttu-id="4faab-113">説明</span><span class="sxs-lookup"><span data-stu-id="4faab-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4faab-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4faab-114">S_OK</span></span>|<span data-ttu-id="4faab-115">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="4faab-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="4faab-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4faab-116">E_INVALIDARG</span></span>|<span data-ttu-id="4faab-117">指定された`pStream`が null です。</span><span class="sxs-lookup"><span data-stu-id="4faab-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="4faab-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4faab-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4faab-119">サイズ`pwzBuffer`が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="4faab-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="4faab-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4faab-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4faab-121">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="4faab-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4faab-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4faab-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4faab-123">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4faab-123">The call timed out.</span></span>|  
|<span data-ttu-id="4faab-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4faab-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4faab-125">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4faab-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4faab-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4faab-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4faab-127">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="4faab-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4faab-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4faab-128">E_FAIL</span></span>|<span data-ttu-id="4faab-129">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4faab-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4faab-130">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4faab-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4faab-131">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="4faab-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4faab-132">要件</span><span class="sxs-lookup"><span data-stu-id="4faab-132">Requirements</span></span>  
 <span data-ttu-id="4faab-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4faab-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4faab-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4faab-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4faab-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4faab-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4faab-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4faab-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4faab-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="4faab-137">See Also</span></span>  
 [<span data-ttu-id="4faab-138">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4faab-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="4faab-139">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4faab-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
