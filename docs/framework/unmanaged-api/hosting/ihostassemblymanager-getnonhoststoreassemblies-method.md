---
title: "IHostAssemblyManager::GetNonHostStoreAssemblies メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager.GetNonHostStoreAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6af013a833ae694aca991f9a71769869cc79b76b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="5c39c-102">IHostAssemblyManager::GetNonHostStoreAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="5c39c-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="5c39c-103">インターフェイス ポインターを取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)ホストが共通言語ランタイム (CLR) の読み込みに必要ですがアセンブリの一覧を表すです。</span><span class="sxs-lookup"><span data-stu-id="5c39c-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c39c-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c39c-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c39c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c39c-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="5c39c-106">[out]アドレスへのポインター、`ICLRAssemblyReferenceList`ホストに読み込む CLR が期待しているアセンブリへの参照のリストを格納します。</span><span class="sxs-lookup"><span data-stu-id="5c39c-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c39c-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c39c-107">Return Value</span></span>  
  
|<span data-ttu-id="5c39c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c39c-108">HRESULT</span></span>|<span data-ttu-id="5c39c-109">説明</span><span class="sxs-lookup"><span data-stu-id="5c39c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c39c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c39c-110">S_OK</span></span>|<span data-ttu-id="5c39c-111">`GetNonHostStoreAssemblies`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="5c39c-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="5c39c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c39c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c39c-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5c39c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c39c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c39c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c39c-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5c39c-115">The call timed out.</span></span>|  
|<span data-ttu-id="5c39c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c39c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c39c-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5c39c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c39c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c39c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c39c-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="5c39c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c39c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c39c-120">E_FAIL</span></span>|<span data-ttu-id="5c39c-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5c39c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c39c-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5c39c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c39c-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="5c39c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5c39c-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5c39c-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5c39c-125">十分なメモリが要求されたの参照の一覧を作成できませんでした。`ICLRAssemblyReferenceList`です。</span><span class="sxs-lookup"><span data-stu-id="5c39c-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c39c-126">コメント</span><span class="sxs-lookup"><span data-stu-id="5c39c-126">Remarks</span></span>  
 <span data-ttu-id="5c39c-127">CLR は、次のガイドラインのセットを使用して参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="5c39c-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
-   <span data-ttu-id="5c39c-128">によって返されるアセンブリ参照の一覧を参照して、最初に、`GetNonHostStoreAssemblies`です。</span><span class="sxs-lookup"><span data-stu-id="5c39c-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
-   <span data-ttu-id="5c39c-129">アセンブリが一覧に表示された場合、CLR は通常どおりにバインドします。</span><span class="sxs-lookup"><span data-stu-id="5c39c-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
-   <span data-ttu-id="5c39c-130">アセンブリが一覧に表示されないと、ホストがの実装を提供されて[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)、CLR 呼び出し[ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)を指定するホストを許可する、バインドするアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="5c39c-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
-   <span data-ttu-id="5c39c-131">それ以外の場合、CLR は、アセンブリのバインドに失敗します。</span><span class="sxs-lookup"><span data-stu-id="5c39c-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="5c39c-132">ホストしている場合`ppReferenceList`、グローバル アセンブリ キャッシュの呼び出しを null、CLR の最初のプローブに`ProvideAssembly`、アセンブリ参照を解決するのには、アプリケーション ベースをプローブとします。</span><span class="sxs-lookup"><span data-stu-id="5c39c-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c39c-133">CLR は呼び出し、初期化時に、 `GetNonHostStoreAssemblies` 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="5c39c-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="5c39c-134">メソッドは再度呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="5c39c-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c39c-135">必要条件</span><span class="sxs-lookup"><span data-stu-id="5c39c-135">Requirements</span></span>  
 <span data-ttu-id="5c39c-136">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c39c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c39c-137">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c39c-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c39c-138">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c39c-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c39c-139">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c39c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c39c-140">参照</span><span class="sxs-lookup"><span data-stu-id="5c39c-140">See Also</span></span>  
 [<span data-ttu-id="5c39c-141">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c39c-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="5c39c-142">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c39c-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="5c39c-143">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c39c-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
