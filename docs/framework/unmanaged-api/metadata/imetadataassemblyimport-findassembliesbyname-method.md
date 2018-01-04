---
title: "IMetaDataAssemblyImport::FindAssembliesByName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6518fdcf1bef8eaea74818f69f46bb6df26e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="50918-102">IMetaDataAssemblyImport::FindAssembliesByName メソッド</span><span class="sxs-lookup"><span data-stu-id="50918-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="50918-103">指定したアセンブリの配列を取得`szAssemblyName`参照の解決には、共通言語ランタイム (CLR) で使用されている標準的な規則を使用して、パラメーター。</span><span class="sxs-lookup"><span data-stu-id="50918-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50918-104">構文</span><span class="sxs-lookup"><span data-stu-id="50918-104">Syntax</span></span>  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50918-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50918-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="50918-106">[in]指定されたアセンブリを検索するためのルート ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="50918-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="50918-107">この値に設定されている場合`null`、`FindAssembliesByName`はグローバル アセンブリ キャッシュでのみアセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="50918-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="50918-108">[in]セミコロンで区切られたサブディレクトリ (たとえば、「bin; bin2」)、アセンブリを検索するためのルート ディレクトリの下の一覧。</span><span class="sxs-lookup"><span data-stu-id="50918-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="50918-109">既定の調査規則で指定されているだけでなく、これらのディレクトリがプローブされます。</span><span class="sxs-lookup"><span data-stu-id="50918-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="50918-110">[in]検索対象のアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="50918-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="50918-111">この文字列の形式が、クラスのリファレンス ページで定義されている<xref:System.Reflection.AssemblyName>です。</span><span class="sxs-lookup"><span data-stu-id="50918-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="50918-112">[in]型の配列 <<!--zzxref:IUnknown --> `IUnknown`> に配置するための`IMetadataAssemblyImport`インターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="50918-112">[in] An array of type <<!--zzxref:IUnknown --> `IUnknown`> in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="50918-113">[out]配置できるインターフェイス ポインターの最大数`ppIUnk`です。</span><span class="sxs-lookup"><span data-stu-id="50918-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="50918-114">[out]インターフェイス ポインターの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="50918-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="50918-115">つまり、インターフェイス ポインターの数が実際に配置`ppIUnk`です。</span><span class="sxs-lookup"><span data-stu-id="50918-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50918-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="50918-116">Return Value</span></span>  
  
|<span data-ttu-id="50918-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50918-117">HRESULT</span></span>|<span data-ttu-id="50918-118">説明</span><span class="sxs-lookup"><span data-stu-id="50918-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="50918-119">`FindAssembliesByName`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="50918-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="50918-120">アセンブリは存在しません。</span><span class="sxs-lookup"><span data-stu-id="50918-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50918-121">コメント</span><span class="sxs-lookup"><span data-stu-id="50918-121">Remarks</span></span>  
 <span data-ttu-id="50918-122">アセンブリ名、付与、`FindAssembliesByName`メソッドは、次のアセンブリ参照を解決するための標準の規則を使用してアセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="50918-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="50918-123">(詳細については、次を参照してください[ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。)。`FindAssembliesByName`により、呼び出し元アセンブリの競合回避モジュール コンテキストのアプリケーション ベースで、プライベート検索パスなどのさまざまな側面を構成します。</span><span class="sxs-lookup"><span data-stu-id="50918-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="50918-124">`FindAssembliesByName`メソッドが、CLR アセンブリ解決ロジックを実行するために、プロセスで初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50918-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="50918-125">そのため、呼び出す必要があります[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT を渡す) 呼び出しの前に`FindAssembliesByName`、して次の呼び出しを[CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="50918-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="50918-126">`FindAssembliesByName`返します、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)に渡される、アセンブリ名のアセンブリ マニフェストを含むファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="50918-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="50918-127">(たとえば、バージョンが含まれていない場合) 特定のアセンブリ名が完全に指定されていない場合は、複数のアセンブリを返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="50918-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="50918-128">`FindAssembliesByName`コンパイル時参照アセンブリを検索しようとするコンパイラで通常使用されます。</span><span class="sxs-lookup"><span data-stu-id="50918-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50918-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="50918-129">Requirements</span></span>  
 <span data-ttu-id="50918-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="50918-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50918-131">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="50918-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50918-132">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="50918-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50918-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50918-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50918-134">参照</span><span class="sxs-lookup"><span data-stu-id="50918-134">See Also</span></span>  
 [<span data-ttu-id="50918-135">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="50918-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="50918-136">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50918-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
