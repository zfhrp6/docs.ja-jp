---
title: "ICorProfilerCallback2::RootReferences2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.RootReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29a5a3051b75df18a08498369aa5707a53caf75f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="993cc-102">ICorProfilerCallback2::RootReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="993cc-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="993cc-103">ガベージ コレクションが発生した後は、ルート参照について、プロファイラーを通知します。</span><span class="sxs-lookup"><span data-stu-id="993cc-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="993cc-104">このメソッドは、の拡張機能、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="993cc-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="993cc-105">構文</span><span class="sxs-lookup"><span data-stu-id="993cc-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="993cc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="993cc-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="993cc-107">[in]内の要素の数、 `rootRefIds`、 `rootKinds`、 `rootFlags`、および`rootIds`配列。</span><span class="sxs-lookup"><span data-stu-id="993cc-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="993cc-108">[in]オブジェクト Id は、静的オブジェクトまたはスタック上のオブジェクトのいずれかの参照の配列。</span><span class="sxs-lookup"><span data-stu-id="993cc-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="993cc-109">内の要素、`rootKinds`配列に対応する要素を分類する情報を提供する、`rootRefIds`配列。</span><span class="sxs-lookup"><span data-stu-id="993cc-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="993cc-110">[in]配列[COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)ガーベッジ コレクション ルートの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="993cc-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="993cc-111">[in]配列[COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)ガーベッジ コレクション ルートのプロパティを記述する値。</span><span class="sxs-lookup"><span data-stu-id="993cc-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="993cc-112">[in]値に応じて、ガーベッジ コレクション ルートについての追加情報を含む整数を指す値 UINT_PTR の配列、`rootKinds`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="993cc-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="993cc-113">ルートの種類が、スタックの場合は、ルート ID は、変数を含む関数です。</span><span class="sxs-lookup"><span data-stu-id="993cc-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="993cc-114">ルート ID が 0 の場合、関数、clr の内部にある名前のない機能です。</span><span class="sxs-lookup"><span data-stu-id="993cc-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="993cc-115">ルートの種類が、ハンドルである場合は、ルート ID は、ガベージ コレクション ハンドルのです。</span><span class="sxs-lookup"><span data-stu-id="993cc-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="993cc-116">その他のルート型の ID 非透過の値は、無視してください。</span><span class="sxs-lookup"><span data-stu-id="993cc-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="993cc-117">コメント</span><span class="sxs-lookup"><span data-stu-id="993cc-117">Remarks</span></span>  
 <span data-ttu-id="993cc-118">`rootRefIds`、 `rootKinds`、 `rootFlags`、および`rootIds`配列は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="993cc-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="993cc-119">つまり、 `rootRefIds[i]`、 `rootKinds[i]`、 `rootFlags[i]`、および`rootIds[i]`すべての対象ルートは同じです。</span><span class="sxs-lookup"><span data-stu-id="993cc-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="993cc-120">両方`RootReferences`と`RootReferences2`をプロファイラーに通知と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="993cc-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="993cc-121">プロファイラーは通常 1 つのメソッドや、他の両方ではなく、ために実装に渡された情報`RootReferences2`に渡されたのスーパー セット`RootReferences`です。</span><span class="sxs-lookup"><span data-stu-id="993cc-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="993cc-122">内のエントリ可能であれば`rootRefIds`を対応するルート参照が null と、マネージ ヒープ上のオブジェクトを参照していないことを意味する 0 にします。</span><span class="sxs-lookup"><span data-stu-id="993cc-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="993cc-123">によって返されるオブジェクト Id`RootReferences2`自体には、コールバック中に無効なため古いアドレスから新しいアドレスにオブジェクトを移動中にガベージ コレクションがある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="993cc-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="993cc-124">このため、`RootReferences2` 呼び出しの間、プロファイラーはオブジェクトを検査するべきではありません。</span><span class="sxs-lookup"><span data-stu-id="993cc-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="993cc-125">ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、すべてのオブジェクトの新しい場所に移動されましたし、安全に検査することができます。</span><span class="sxs-lookup"><span data-stu-id="993cc-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="993cc-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="993cc-126">Requirements</span></span>  
 <span data-ttu-id="993cc-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="993cc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="993cc-128">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="993cc-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="993cc-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="993cc-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="993cc-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="993cc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993cc-131">参照</span><span class="sxs-lookup"><span data-stu-id="993cc-131">See Also</span></span>  
 [<span data-ttu-id="993cc-132">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="993cc-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="993cc-133">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="993cc-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
