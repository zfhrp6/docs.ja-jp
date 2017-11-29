---
title: "IALink インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: IALink
helpviewer_keywords: IALink interface
ms.assetid: 50abd02d-6488-4815-999b-4fb89af4d568
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8864e33fa281f69b72af12276ed31e5e543045ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ialink-interface"></a><span data-ttu-id="2e2d2-102">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e2d2-102">IALink Interface</span></span>
<span data-ttu-id="2e2d2-103">.NET Framework アセンブリを構築する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2e2d2-103">Helps in constructing .NET Framework assemblies.</span></span> <span data-ttu-id="2e2d2-104">特に、インターフェイスには、マルチ モジュール アセンブリのアセンブリ マニフェストの作成、厳密な名前によるアセンブリの署名および netmodule の作成を補助するメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2e2d2-104">Among other things, the interface contains methods that assist in writing assembly manifests for multi-module assemblies, signing assemblies with strong names, and creating netmodules.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e2d2-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2e2d2-105">In This Section</span></span>  
 [<span data-ttu-id="2e2d2-106">AddFile Method1</span><span class="sxs-lookup"><span data-stu-id="2e2d2-106">AddFile Method1</span></span>](../../../../docs/framework/unmanaged-api/alink/addfile-method.md)  
  
 [<span data-ttu-id="2e2d2-107">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="2e2d2-107">AddImport Method1</span></span>](../../../../docs/framework/unmanaged-api/alink/addimport-method.md)  
  
 [<span data-ttu-id="2e2d2-108">CloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-108">CloseAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/alink/closeassembly-method.md)  
  
 [<span data-ttu-id="2e2d2-109">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-109">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/alink/closeenum-method.md)  
  
 [<span data-ttu-id="2e2d2-110">EmbedResource メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-110">EmbedResource Method</span></span>](../../../../docs/framework/unmanaged-api/alink/embedresource-method.md)  
  
 [<span data-ttu-id="2e2d2-111">EmitAssemblyCustomAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-111">EmitAssemblyCustomAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/alink/emitassemblycustomattribute-method.md)  
  
 [<span data-ttu-id="2e2d2-112">EmitManifest メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-112">EmitManifest Method</span></span>](../../../../docs/framework/unmanaged-api/alink/emitmanifest-method.md)  
  
 [<span data-ttu-id="2e2d2-113">EndMerge メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-113">EndMerge Method</span></span>](../../../../docs/framework/unmanaged-api/alink/endmerge-method.md)  
  
 [<span data-ttu-id="2e2d2-114">EnumCustomAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-114">EnumCustomAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/alink/enumcustomattributes-method.md)  
  
 [<span data-ttu-id="2e2d2-115">EnumImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-115">EnumImportTypes Method</span></span>](../../../../docs/framework/unmanaged-api/alink/enumimporttypes-method.md)  
  
 [<span data-ttu-id="2e2d2-116">ExportNestedType メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-116">ExportNestedType Method</span></span>](../../../../docs/framework/unmanaged-api/alink/exportnestedtype-method.md)  
  
 [<span data-ttu-id="2e2d2-117">ExportNestedTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-117">ExportNestedTypeForwarder Method</span></span>](../../../../docs/framework/unmanaged-api/alink/exportnestedtypeforwarder-method.md)  
  
 [<span data-ttu-id="2e2d2-118">ExportType メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-118">ExportType Method</span></span>](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md)  
  
 [<span data-ttu-id="2e2d2-119">ExportTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-119">ExportTypeForwarder Method</span></span>](../../../../docs/framework/unmanaged-api/alink/exporttypeforwarder-method.md)  
  
 [<span data-ttu-id="2e2d2-120">FreeWin32ResBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-120">FreeWin32ResBlob Method</span></span>](../../../../docs/framework/unmanaged-api/alink/freewin32resblob-method.md)  
  
 [<span data-ttu-id="2e2d2-121">GetAssemblyRefHash メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-121">GetAssemblyRefHash Method</span></span>](../../../../docs/framework/unmanaged-api/alink/getassemblyrefhash-method.md)  
  
 [<span data-ttu-id="2e2d2-122">GetResolutionScope メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-122">GetResolutionScope Method</span></span>](../../../../docs/framework/unmanaged-api/alink/getresolutionscope-method.md)  
  
 [<span data-ttu-id="2e2d2-123">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="2e2d2-123">GetScope Method1</span></span>](../../../../docs/framework/unmanaged-api/alink/getscope-method.md)  
  
 [<span data-ttu-id="2e2d2-124">GetWin32ResBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-124">GetWin32ResBlob Method</span></span>](../../../../docs/framework/unmanaged-api/alink/getwin32resblob-method.md)  
  
 [<span data-ttu-id="2e2d2-125">ImportFile メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-125">ImportFile Method</span></span>](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)  
  
 [<span data-ttu-id="2e2d2-126">ImportFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-126">ImportFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/alink/importfile2-method.md)  
  
 [<span data-ttu-id="2e2d2-127">ImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-127">ImportTypes Method</span></span>](../../../../docs/framework/unmanaged-api/alink/importtypes-method.md)  
  
 <span data-ttu-id="2e2d2-128">「Init メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-128">"Init Method"</span></span>  
  
 [<span data-ttu-id="2e2d2-129">LinkResource メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-129">LinkResource Method</span></span>](../../../../docs/framework/unmanaged-api/alink/linkresource-method.md)  
  
 [<span data-ttu-id="2e2d2-130">PreCloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-130">PreCloseAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/alink/precloseassembly-method.md)  
  
 [<span data-ttu-id="2e2d2-131">SetAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-131">SetAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/alink/setassemblyfile-method.md)  
  
 [<span data-ttu-id="2e2d2-132">SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-132">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/alink/setassemblyprops-method.md)  
  
 [<span data-ttu-id="2e2d2-133">SetNonAssemblyFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="2e2d2-133">SetNonAssemblyFlags Method</span></span>](../../../../docs/framework/unmanaged-api/alink/setnonassemblyflags-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="2e2d2-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e2d2-134">See Also</span></span>  
 [<span data-ttu-id="2e2d2-135">ALink API</span><span class="sxs-lookup"><span data-stu-id="2e2d2-135">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="2e2d2-136">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e2d2-136">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2e2d2-137">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="2e2d2-137">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
