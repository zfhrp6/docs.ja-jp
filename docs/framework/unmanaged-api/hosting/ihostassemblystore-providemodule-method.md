---
title: IHostAssemblyStore::ProvideModule メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b604e1d7fc3d3c8adf7d95bd95843bc0110dbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440019"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="ac7cd-102">IHostAssemblyStore::ProvideModule メソッド</span><span class="sxs-lookup"><span data-stu-id="ac7cd-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="ac7cd-103">アセンブリとリンク (ではありません、埋め込み) 内のモジュール リソース ファイルを解決します。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac7cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="ac7cd-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac7cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac7cd-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="ac7cd-106">[in]ポインター、 [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) 、要求されたモジュールを記述するインスタンス<xref:System.AppDomain>アセンブリ、およびモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="ac7cd-107">[out]一意の識別子へのポインター、`IStream`読み込まれたモジュールを含むです。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="ac7cd-108">[out]アドレスへのポインター、`IStream`オブジェクト、読み込まれるポータブル実行可能 (PE) イメージが含まれていますか、モジュールが見つからなかった場合は null です。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="ac7cd-109">[out]アドレスへのポインター、`IStream`オブジェクトを要求されたモジュールのデバッグ (PDB) 情報をプログラムを含むまたは null の場合、.pdb ファイルが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac7cd-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac7cd-110">Return Value</span></span>  
  
|<span data-ttu-id="ac7cd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac7cd-111">HRESULT</span></span>|<span data-ttu-id="ac7cd-112">説明</span><span class="sxs-lookup"><span data-stu-id="ac7cd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac7cd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac7cd-113">S_OK</span></span>|<span data-ttu-id="ac7cd-114">`ProvideModule` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="ac7cd-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac7cd-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac7cd-116">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac7cd-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac7cd-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac7cd-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-118">The call timed out.</span></span>|  
|<span data-ttu-id="ac7cd-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac7cd-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac7cd-120">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac7cd-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac7cd-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac7cd-122">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac7cd-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac7cd-123">E_FAIL</span></span>|<span data-ttu-id="ac7cd-124">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac7cd-125">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac7cd-126">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ac7cd-127">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="ac7cd-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="ac7cd-128">要求されたアセンブリまたはリンクされたリソースを配置できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="ac7cd-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ac7cd-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ac7cd-130">`pdwModuleId` ホストを返す必要がある識別子を格納するのに十分な大きさがないです。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac7cd-131">コメント</span><span class="sxs-lookup"><span data-stu-id="ac7cd-131">Remarks</span></span>  
 <span data-ttu-id="ac7cd-132">Id 値が返される`pdwModuleId`ホストによって指定します。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="ac7cd-133">識別子は、プロセスの有効期間内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="ac7cd-134">CLR は、この値を関連付けられているストリームの一意識別子として使用します。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="ac7cd-135">値に対して各値をチェック`pAssemblyId`への呼び出しによって返される[ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)の値に対して`pdwModuleId`を他の呼び出しによって返される`ProvideModule`です。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="ac7cd-136">別のホストが同じ識別子の値を返す場合`IStream`CLR では、そのストリームの内容が既にマップされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="ac7cd-137">場合は、CLR は、新しいものをマップする代わりにイメージの既存のコピーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="ac7cd-138">したがって、識別子も重複していないから返されたアセンブリ識別子を持つ`ProvideAssembly`します。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac7cd-139">要件</span><span class="sxs-lookup"><span data-stu-id="ac7cd-139">Requirements</span></span>  
 <span data-ttu-id="ac7cd-140">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac7cd-141">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac7cd-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac7cd-142">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ac7cd-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac7cd-143">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac7cd-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7cd-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac7cd-144">See Also</span></span>  
 [<span data-ttu-id="ac7cd-145">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac7cd-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="ac7cd-146">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac7cd-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="ac7cd-147">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac7cd-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
