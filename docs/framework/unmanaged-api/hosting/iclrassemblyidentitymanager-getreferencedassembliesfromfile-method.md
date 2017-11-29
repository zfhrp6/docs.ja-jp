---
title: "ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abd80676fe459bd779d5fad4cf2e9c41e140741b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="f4d9d-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="f4d9d-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="f4d9d-103">取得、 [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)インスタンスを指定したファイル パスにあるアセンブリによって参照されるアセンブリの一覧を含むです。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d9d-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4d9d-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4d9d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4d9d-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="f4d9d-106">[in]評価するアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f4d9d-107">[in]将来の機能拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="f4d9d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンをサポートする唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="f4d9d-109">[in]ポインター、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)から除外するアセンブリを表すオブジェクト`ppReferenceEnum`です。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="f4d9d-110">[out]アドレスへのポインター、`ICLRReferenceAssemblyEnum`のアセンブリによって参照されるアセンブリのアセンブリ id データを格納しているオブジェクト`pwzFilePath`、によって表されるアセンブリを除く`pExcludeAssembliesList`です。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4d9d-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="f4d9d-111">Return Value</span></span>  
  
|<span data-ttu-id="f4d9d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4d9d-112">HRESULT</span></span>|<span data-ttu-id="f4d9d-113">説明</span><span class="sxs-lookup"><span data-stu-id="f4d9d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4d9d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4d9d-114">S_OK</span></span>|<span data-ttu-id="f4d9d-115">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="f4d9d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f4d9d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f4d9d-117">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f4d9d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f4d9d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f4d9d-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-119">The call timed out.</span></span>|  
|<span data-ttu-id="f4d9d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f4d9d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f4d9d-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f4d9d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f4d9d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f4d9d-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f4d9d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4d9d-124">E_FAIL</span></span>|<span data-ttu-id="f4d9d-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f4d9d-126">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f4d9d-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4d9d-128">コメント</span><span class="sxs-lookup"><span data-stu-id="f4d9d-128">Remarks</span></span>  
 <span data-ttu-id="f4d9d-129">呼び出し元は、返された一覧から既知のアセンブリ参照のセットを除外するを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="f4d9d-130">このセットがによって定義された、`pExcludeAssembliesList`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4d9d-131">要件</span><span class="sxs-lookup"><span data-stu-id="f4d9d-131">Requirements</span></span>  
 <span data-ttu-id="f4d9d-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4d9d-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4d9d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4d9d-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4d9d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4d9d-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4d9d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d9d-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4d9d-136">See Also</span></span>  
 [<span data-ttu-id="f4d9d-137">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4d9d-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="f4d9d-138">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4d9d-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="f4d9d-139">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4d9d-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
