---
title: "ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aae8c16430f8139601a5faa2bad42e285bceb84b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="a4991-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="a4991-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="a4991-103">ポインターを取得、 [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)指定のストリーム内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納しているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a4991-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4991-104">構文</span><span class="sxs-lookup"><span data-stu-id="a4991-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4991-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4991-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="a4991-106">[in]インターフェイス ポインター、`IStream`に評価されるアセンブリを含むです。</span><span class="sxs-lookup"><span data-stu-id="a4991-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a4991-107">[in]将来の機能拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="a4991-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="a4991-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンをサポートする唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="a4991-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="a4991-109">[in]ポインター、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)から除外するアセンブリのアセンブリ id データを格納しているオブジェクト`ppReferenceEnum`です。</span><span class="sxs-lookup"><span data-stu-id="a4991-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="a4991-110">[out]アドレスへのポインター、`ICLRReferenceAssemblyEnum`内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納しているオブジェクト`pStream`、内のアセンブリを除く`pExcludeAssembliesList`です。</span><span class="sxs-lookup"><span data-stu-id="a4991-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4991-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="a4991-111">Return Value</span></span>  
  
|<span data-ttu-id="a4991-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4991-112">HRESULT</span></span>|<span data-ttu-id="a4991-113">説明</span><span class="sxs-lookup"><span data-stu-id="a4991-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4991-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4991-114">S_OK</span></span>|<span data-ttu-id="a4991-115">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a4991-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="a4991-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a4991-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a4991-117">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="a4991-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a4991-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a4991-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a4991-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a4991-119">The call timed out.</span></span>|  
|<span data-ttu-id="a4991-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a4991-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a4991-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a4991-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a4991-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a4991-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a4991-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="a4991-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a4991-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4991-124">E_FAIL</span></span>|<span data-ttu-id="a4991-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a4991-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a4991-126">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a4991-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a4991-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="a4991-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4991-128">コメント</span><span class="sxs-lookup"><span data-stu-id="a4991-128">Remarks</span></span>  
 <span data-ttu-id="a4991-129">呼び出し元は、返された一覧から既知のアセンブリ参照のセットを除外するを選択できます。</span><span class="sxs-lookup"><span data-stu-id="a4991-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="a4991-130">このセットがによって定義された`pExcludeAssembliesList`です。</span><span class="sxs-lookup"><span data-stu-id="a4991-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4991-131">必要条件</span><span class="sxs-lookup"><span data-stu-id="a4991-131">Requirements</span></span>  
 <span data-ttu-id="a4991-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4991-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4991-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4991-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4991-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4991-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4991-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4991-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4991-136">参照</span><span class="sxs-lookup"><span data-stu-id="a4991-136">See Also</span></span>  
 [<span data-ttu-id="a4991-137">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4991-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="a4991-138">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4991-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="a4991-139">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4991-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
