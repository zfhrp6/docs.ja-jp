---
title: "メタデータ インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4043bdb7ea128e7ac34349dad8c51a0b247df71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-interfaces"></a><span data-ttu-id="4749b-102">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-102">Metadata Interfaces</span></span>
<span data-ttu-id="4749b-103">このセクションでは、.NET Framework の型、メソッド、フィールドなどによって公開されるメタデータにアクセスできるようにするアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4749b-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4749b-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4749b-104">In This Section</span></span>  
 [<span data-ttu-id="4749b-105">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="4749b-106">動的なコード コンパイルのためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="4749b-107">IHostFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="4749b-108">ランタイム ホストがメタデータ トークンに処理済みのマークを付けるためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="4749b-109">IMapToken インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="4749b-110">インポートされたメタデータ署名と生成されたメタデータ署名との間の割り当て機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="4749b-111">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="4749b-112">共通言語ランタイム (CLR) がリソースの解決および消費に使用する自己記述モデルをサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="4749b-113">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="4749b-114">アセンブリ マニフェストの内容にアクセスして確認するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="4749b-115">IMetaDataConverter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="4749b-116">タイプ ライブラリをそれぞれのメタデータ署名にマップして、一方から他方に変換するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="4749b-117">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="4749b-118">`IMetaDataDispenser` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="4749b-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="4749b-119">代わりに、`IMetaDataDispenserEx` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="4749b-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="4749b-120">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="4749b-121">メタデータを作成または変更するためのメモリ領域を割り当てるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="4749b-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="4749b-123">現在定義されているスコープ内のアセンブリについてのメタデータを作成、変更、格納するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="4749b-124">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="4749b-125"><xref:System.Type?displayProperty=nameWithType> 型のパラメーターを持つメソッドおよびコンストラクターのメタデータ署名を定義および変更するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="4749b-126">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="4749b-127">アセンブリのメタデータ署名の解決時のエラーを報告するためのコールバック機構を提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="4749b-128">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="4749b-129">メタデータ トークンにマークを付け、フィルター処理をして、既に実行されたアクションが繰り返し行われないようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="4749b-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="4749b-131">他のアセンブリの型をインポートおよび操作するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="4749b-132">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="4749b-133">`IMetaDataImport` を拡張して、ジェネリック型を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4749b-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="4749b-134">IMetaDataInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="4749b-135">ディスク上のファイルからメモリへのメタデータのマッピングに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="4749b-136">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="4749b-137">テーブル内のメタデータ情報の格納と取得のためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="4749b-138">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="4749b-139">`IMetaDataTables` を拡張して、メタデータ ストリームを使用するためのメソッドを含めます。</span><span class="sxs-lookup"><span data-stu-id="4749b-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="4749b-140">IMetaDataValidate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4749b-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="4749b-141">メタデータ署名の検証で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4749b-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4749b-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="4749b-142">Related Sections</span></span>  
 [<span data-ttu-id="4749b-143">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="4749b-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="4749b-144">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="4749b-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="4749b-145">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="4749b-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="4749b-146">メタデータ共用体</span><span class="sxs-lookup"><span data-stu-id="4749b-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
