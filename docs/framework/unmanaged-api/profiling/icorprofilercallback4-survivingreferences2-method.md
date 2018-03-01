---
title: "ICorProfilerCallback4::SurvivingReferences2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db40e908421c45e9d4192c436995d8137f81ec0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="dc666-102">ICorProfilerCallback4::SurvivingReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="dc666-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="dc666-103">非圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトのレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="dc666-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="dc666-104">このメソッドは、プロファイラーが実装されている場合、 [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="dc666-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="dc666-105">このコールバックが置き換えられます、 [icorprofilercallback 2::survivingreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)メソッド、ULONG で表現できる内容を超える長さのオブジェクトの大きい範囲を報告できるためです。</span><span class="sxs-lookup"><span data-stu-id="dc666-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc666-106">構文</span><span class="sxs-lookup"><span data-stu-id="dc666-106">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc666-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc666-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="dc666-108">[in] 非圧縮ガベージ コレクションを実行した後に存続する、隣接したオブジェクトのブロック数。</span><span class="sxs-lookup"><span data-stu-id="dc666-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="dc666-109">つまり、`cSurvivingObjectIDRanges` の値は、`objectIDRangeStart` 配列と `cObjectIDRangeLength` 配列のサイズを表します。これらの配列にはそれぞれ、オブジェクトの各ブロックの `ObjectID` と長さが格納されます。</span><span class="sxs-lookup"><span data-stu-id="dc666-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="dc666-110">`SurvivingReferences2` の次の2個の引数は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="dc666-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="dc666-111">つまり、`objectIDRangeStart` と `cObjectIDRangeLength` は隣接するオブジェクトの同じブロックを対象としています。</span><span class="sxs-lookup"><span data-stu-id="dc666-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="dc666-112">[in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの開始アドレスを表す、`ObjectID` 値の配列。</span><span class="sxs-lookup"><span data-stu-id="dc666-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="dc666-113">[in] それぞれがメモリ内に存続する隣接オブジェクト ブロックのサイズを表す、整数の配列。</span><span class="sxs-lookup"><span data-stu-id="dc666-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="dc666-114">サイズは、`objectIDRangeStart` 配列内の参照される各ブロックに対して指定します。</span><span class="sxs-lookup"><span data-stu-id="dc666-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc666-115">コメント</span><span class="sxs-lookup"><span data-stu-id="dc666-115">Remarks</span></span>  
 <span data-ttu-id="dc666-116">`objectIDRangeStart` 配列と `cObjectIDRangeLength` 配列の要素は、次のように解釈されて、ガベージ コレクションでオブジェクトが存続したかどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc666-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="dc666-117">`ObjectID` 値 (`ObjectID`) が次の範囲内にあるとします。</span><span class="sxs-lookup"><span data-stu-id="dc666-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="dc666-118">次の範囲内にある `i` のすべての値について、オブジェクトはガベージ コレクションの実行後に存続しています。</span><span class="sxs-lookup"><span data-stu-id="dc666-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="dc666-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="dc666-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="dc666-120">非圧縮ガベージ コレクションは、"無効な" オブジェクトによって占有されているメモリをクリアしますが、解放された領域は圧縮しません。</span><span class="sxs-lookup"><span data-stu-id="dc666-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="dc666-121">そのため、メモリはヒープに返されますが、"有効な" オブジェクトは移動されません。</span><span class="sxs-lookup"><span data-stu-id="dc666-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="dc666-122">共通言語ランタイム (CLR: Common Language Runtime) は、非圧縮ガベージ コレクションに対して `SurvivingReferences2` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="dc666-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="dc666-123">圧縮ガベージ コレクション、 [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)は代わりに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="dc666-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="dc666-124">単一のガベージ コレクションで 1 つのジェネレーションを圧縮できますが、その他のジェネレーションは非圧縮になります。</span><span class="sxs-lookup"><span data-stu-id="dc666-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="dc666-125">特定のジェネレーションに対してガベージ コレクションは、プロファイラーがいずれかを受け取り、`SurvivingReferences2`コールバックまたは[MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)コールバックが、両方は使用できません。</span><span class="sxs-lookup"><span data-stu-id="dc666-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="dc666-126">特定のガベージ コレクションで複数の `SurvivingReferences2` コールバックを受け取ることがあります。この原因としては、内部バッファリングの制限、サーバーのガベージ コレクション中の複数のコールバックなどが考えられます。</span><span class="sxs-lookup"><span data-stu-id="dc666-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="dc666-127">あるガベージ コレクションで複数のコールバックが生じる場合、情報が累積されます。つまり、`SurvivingReferences2` コールバックで報告されるすべての参照は対象のガベージ コレクション後も存続します。</span><span class="sxs-lookup"><span data-stu-id="dc666-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="dc666-128">プロファイラーでは、両方を実装する場合、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)と[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) 、インターフェイス、`SurvivingReferences2`メソッドは、前に呼び出されます、 [ICorProfilerCallback2:。SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)場合に限り、メソッド、`SurvivingReferences2`が正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="dc666-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="dc666-129">プロファイラーは HRESULT を返すことがあり、これは `SurvivingReferences2` メソッドの失敗を示し、2 番目のメソッドが呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="dc666-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc666-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="dc666-130">Requirements</span></span>  
 <span data-ttu-id="dc666-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dc666-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc666-132">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc666-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc666-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc666-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc666-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc666-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc666-135">参照</span><span class="sxs-lookup"><span data-stu-id="dc666-135">See Also</span></span>  
 [<span data-ttu-id="dc666-136">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc666-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dc666-137">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc666-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="dc666-138">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc666-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
