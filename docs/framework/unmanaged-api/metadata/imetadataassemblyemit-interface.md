---
title: "IMetaDataAssemblyEmit インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit
helpviewer_keywords: IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af7a5fd5a564aa7366924f47b0c526aff7153521
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="130b0-102">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="130b0-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="130b0-103">共通言語ランタイムがリソースの解決および消費に使用する自己記述モデルをサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="130b0-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="130b0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-104">Methods</span></span>  
  
|<span data-ttu-id="130b0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-105">Method</span></span>|<span data-ttu-id="130b0-106">説明</span><span class="sxs-lookup"><span data-stu-id="130b0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="130b0-107">DefineAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="130b0-108">指定したアセンブリのメタデータを含むアセンブリ データ構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="130b0-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="130b0-109">DefineAssemblyRef メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="130b0-110">このアセンブリが参照するアセンブリのメタデータを含む `AssemblyRef` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="130b0-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="130b0-111">DefineExportedType メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="130b0-112">指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="130b0-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="130b0-113">DefineFile メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="130b0-114">このアセンブリが参照するアセンブリのメタデータを含む `File` メタデータ構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="130b0-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="130b0-115">DefineManifestResource メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="130b0-116">指定したマニフェスト リソースのメタデータを含む `ManifestResource` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="130b0-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="130b0-117">SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="130b0-118">指定された `Assembly` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="130b0-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="130b0-119">SetAssemblyRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="130b0-120">指定された `AssemblyRef` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="130b0-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="130b0-121">SetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="130b0-122">指定された `ExportedType` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="130b0-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="130b0-123">SetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="130b0-124">指定された `File` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="130b0-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="130b0-125">SetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="130b0-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="130b0-126">指定された `ManifestResource` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="130b0-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="130b0-127">コメント</span><span class="sxs-lookup"><span data-stu-id="130b0-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="130b0-128">要件</span><span class="sxs-lookup"><span data-stu-id="130b0-128">Requirements</span></span>  
 <span data-ttu-id="130b0-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="130b0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="130b0-130">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="130b0-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="130b0-131">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="130b0-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="130b0-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="130b0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130b0-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="130b0-133">See Also</span></span>  
 [<span data-ttu-id="130b0-134">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="130b0-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="130b0-135">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="130b0-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
