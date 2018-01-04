---
title: "ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f255db046f4c7d698ad864723167e81952481519
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="d942c-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference メソッド</span><span class="sxs-lookup"><span data-stu-id="d942c-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="d942c-103">取得、 [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)列挙子を指定した id の種類を持つアセンブリによって参照されるアセンブリの id。</span><span class="sxs-lookup"><span data-stu-id="d942c-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d942c-104">構文</span><span class="sxs-lookup"><span data-stu-id="d942c-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d942c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d942c-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="d942c-106">[in]WinNT.h で定義されているプロセッサ アーキテクチャを指定する有効な値です。</span><span class="sxs-lookup"><span data-stu-id="d942c-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d942c-107">[in]将来の機能拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="d942c-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="d942c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンをサポートする唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="d942c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="d942c-109">[in]通常の呼び出しから返される、不透明なアセンブリ バインド id、 [iclrassemblyidentitymanager::getbindingidentityfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)または[iclrassemblyidentitymanager::getbindingidentityfromstream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d942c-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="d942c-110">[out]インターフェイス ポインター、`ICLRProbingAssemblyEnum`によって示されているアセンブリによって参照されるアセンブリへの参照を含む列挙子`pwzReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="d942c-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d942c-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="d942c-111">Return Value</span></span>  
  
|<span data-ttu-id="d942c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d942c-112">HRESULT</span></span>|<span data-ttu-id="d942c-113">説明</span><span class="sxs-lookup"><span data-stu-id="d942c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d942c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d942c-114">S_OK</span></span>|<span data-ttu-id="d942c-115">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="d942c-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="d942c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d942c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d942c-117">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="d942c-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d942c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d942c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d942c-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d942c-119">The call timed out.</span></span>|  
|<span data-ttu-id="d942c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d942c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d942c-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d942c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d942c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d942c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d942c-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="d942c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d942c-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d942c-124">E_FAIL</span></span>|<span data-ttu-id="d942c-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d942c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d942c-126">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="d942c-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d942c-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="d942c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d942c-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="d942c-128">Requirements</span></span>  
 <span data-ttu-id="d942c-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d942c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d942c-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d942c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d942c-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d942c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d942c-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d942c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d942c-133">参照</span><span class="sxs-lookup"><span data-stu-id="d942c-133">See Also</span></span>  
 [<span data-ttu-id="d942c-134">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d942c-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="d942c-135">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d942c-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d942c-136">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d942c-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
