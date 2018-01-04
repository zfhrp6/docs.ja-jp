---
title: "ICorDebugSymbolProvider インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63823c535ad4d036dd5d539c8fe5381d350ccbe5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="59b4c-102">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59b4c-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="59b4c-103">デバッグ シンボル情報を取得するために使用できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59b4c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-104">Methods</span></span>  
  
|<span data-ttu-id="59b4c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-105">Method</span></span>|<span data-ttu-id="59b4c-106">説明</span><span class="sxs-lookup"><span data-stu-id="59b4c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59b4c-107">GetAssemblyImageBytes メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-107">GetAssemblyImageBytes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="59b4c-108">マージされたアセンブリ内の指定の相対仮想アドレス (RVA: relative virtual address) で、マージされたアセンブリのデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="59b4c-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="59b4c-109">GetAssemblyImageMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-109">GetAssemblyImageMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="59b4c-110">マージされたアセンブリのメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="59b4c-111">GetCodeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-111">GetCodeRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="59b4c-112">メソッド内の指定の相対仮想アドレス (RVA: relative virtual address) で、メソッド開始アドレスとサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="59b4c-113">GetInstanceFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-113">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="59b4c-114">typespec シグネチャに対応するインスタンス フィールド シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="59b4c-115">GetMergedAssemblyRecords メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-115">GetMergedAssemblyRecords Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="59b4c-116">すべてのマージされたアセンブリのシンボル レコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="59b4c-117">GetMethodLocalSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-117">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="59b4c-118">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのローカル シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="59b4c-119">GetMethodParameterSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-119">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="59b4c-120">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのパラメーター シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="59b4c-121">GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="59b4c-122">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのプロパティに関する情報 (メソッドのメタデータ トークンなど) と、そのジェネリック パラメーターに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="59b4c-123">GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-123">GetObjectSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="59b4c-124">typespec シグネチャに基づいてオブジェクトのオブジェクト サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="59b4c-125">GetStaticFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-125">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="59b4c-126">typespec シグネチャに対応する静的フィールド シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="59b4c-127">GetTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="59b4c-127">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="59b4c-128">Vtable の指定の相対仮想アドレス (RVA) における、ジェネリック パラメーターのシグネチャの数など、型のプロパティに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59b4c-129">コメント</span><span class="sxs-lookup"><span data-stu-id="59b4c-129">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59b4c-130">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="59b4c-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="59b4c-131">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="59b4c-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59b4c-132">必要条件</span><span class="sxs-lookup"><span data-stu-id="59b4c-132">Requirements</span></span>  
 <span data-ttu-id="59b4c-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="59b4c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59b4c-134">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59b4c-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59b4c-135">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59b4c-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59b4c-136">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59b4c-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b4c-137">参照</span><span class="sxs-lookup"><span data-stu-id="59b4c-137">See Also</span></span>  
 [<span data-ttu-id="59b4c-138">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59b4c-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="59b4c-139">デバッグ</span><span class="sxs-lookup"><span data-stu-id="59b4c-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
