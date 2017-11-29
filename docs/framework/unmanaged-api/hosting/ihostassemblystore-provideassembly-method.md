---
title: "IHostAssemblyStore::ProvideAssembly メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore.ProvideAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cda88c2e93b4f90844ad3dec2ed0fa4366dba6d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="513ff-102">IHostAssemblyStore::ProvideAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="513ff-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="513ff-103">によって参照されているアセンブリへの参照を取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)から返された[ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="513ff-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="513ff-104">共通言語ランタイム (CLR) を呼び出す`ProvideAssembly`一覧に表示されていないアセンブリごとにします。</span><span class="sxs-lookup"><span data-stu-id="513ff-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="513ff-105">構文</span><span class="sxs-lookup"><span data-stu-id="513ff-105">Syntax</span></span>  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="513ff-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="513ff-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="513ff-107">[in]ポインター、 [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)ホストを使用して、任意のバージョン管理ポリシーの存在の有無を含め、特定のバインド特性を判別するインスタンスにバインドするアセンブリとします。</span><span class="sxs-lookup"><span data-stu-id="513ff-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="513ff-108">[out]この要求されたアセンブリの一意の識別子へのポインター`IStream`です。</span><span class="sxs-lookup"><span data-stu-id="513ff-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="513ff-109">[out]プラットフォームがなくても要求されたアセンブリの証拠の決定に使用されるホストに固有のデータへのポインターでは、呼び出しが発生します。</span><span class="sxs-lookup"><span data-stu-id="513ff-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="513ff-110">`pHostContext`対応する、<xref:System.Reflection.Assembly.HostContext%2A>マネージ プロパティ<xref:System.Reflection.Assembly>クラスです。</span><span class="sxs-lookup"><span data-stu-id="513ff-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="513ff-111">[out]アドレスへのポインター、`IStream`ポータブル実行可能 (PE) イメージを読み込む、またはアセンブリが見つからなかった場合は null を格納しています。</span><span class="sxs-lookup"><span data-stu-id="513ff-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="513ff-112">[out]アドレスへのポインター、`IStream`を格納しているプログラムのデバッグ (PDB) の情報、または null 場合、.pdb ファイルが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="513ff-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="513ff-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="513ff-113">Return Value</span></span>  
  
|<span data-ttu-id="513ff-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="513ff-114">HRESULT</span></span>|<span data-ttu-id="513ff-115">説明</span><span class="sxs-lookup"><span data-stu-id="513ff-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="513ff-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="513ff-116">S_OK</span></span>|<span data-ttu-id="513ff-117">`ProvideAssembly`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="513ff-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="513ff-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="513ff-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="513ff-119">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="513ff-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="513ff-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="513ff-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="513ff-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="513ff-121">The call timed out.</span></span>|  
|<span data-ttu-id="513ff-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="513ff-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="513ff-123">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="513ff-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="513ff-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="513ff-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="513ff-125">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="513ff-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="513ff-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="513ff-126">E_FAIL</span></span>|<span data-ttu-id="513ff-127">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="513ff-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="513ff-128">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="513ff-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="513ff-129">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="513ff-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="513ff-130">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="513ff-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="513ff-131">要求されたアセンブリが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="513ff-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="513ff-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="513ff-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="513ff-133">によって指定されたバッファー サイズ`pAssemblyId`に返す必要が、ホストの識別子を保持するのに十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="513ff-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="513ff-134">コメント</span><span class="sxs-lookup"><span data-stu-id="513ff-134">Remarks</span></span>  
 <span data-ttu-id="513ff-135">Id 値が返される`pAssemblyId`ホストによって指定します。</span><span class="sxs-lookup"><span data-stu-id="513ff-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="513ff-136">識別子は、プロセスの有効期間内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="513ff-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="513ff-137">CLR は、この値をストリームの一意の識別子として使用します。</span><span class="sxs-lookup"><span data-stu-id="513ff-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="513ff-138">値に対して各値をチェック`pAssemblyId`を他の呼び出しによって返される`ProvideAssembly`です。</span><span class="sxs-lookup"><span data-stu-id="513ff-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="513ff-139">場合は、ホストは、同じを返します`pAssemblyId`別の値`IStream`CLR では、そのストリームの内容が既にマップされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="513ff-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="513ff-140">場合は、ランタイムは新しい 1 つのマッピングではなく、イメージの既存のコピーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="513ff-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="513ff-141">要件</span><span class="sxs-lookup"><span data-stu-id="513ff-141">Requirements</span></span>  
 <span data-ttu-id="513ff-142">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="513ff-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="513ff-143">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="513ff-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="513ff-144">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="513ff-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="513ff-145">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="513ff-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513ff-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="513ff-146">See Also</span></span>  
 [<span data-ttu-id="513ff-147">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="513ff-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="513ff-148">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="513ff-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="513ff-149">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="513ff-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
