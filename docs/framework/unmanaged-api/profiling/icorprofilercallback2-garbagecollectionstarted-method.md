---
title: ICorProfilerCallback2::GarbageCollectionStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a447dca98e5010163d5cc5f4f3da4333f4cdf7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455271"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="c5c63-102">ICorProfilerCallback2::GarbageCollectionStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="c5c63-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="c5c63-103">ガベージ コレクションが開始されたことをコード プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c5c63-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c63-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5c63-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5c63-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5c63-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="c5c63-106">[in]内のエントリの総数、`generationCollected`配列。</span><span class="sxs-lookup"><span data-stu-id="c5c63-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="c5c63-107">[in]ブール型の値の配列`true`このガベージ コレクションによって収集された、それ以外の配列インデックスに対応する生成されている場合`false`です。</span><span class="sxs-lookup"><span data-stu-id="c5c63-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="c5c63-108">配列のインデックスの値を[COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)列挙体は、生成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c5c63-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="c5c63-109">[in]値、 [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)をガベージ コレクションの理由を示す列挙体が発生しました。</span><span class="sxs-lookup"><span data-stu-id="c5c63-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5c63-110">コメント</span><span class="sxs-lookup"><span data-stu-id="c5c63-110">Remarks</span></span>  
 <span data-ttu-id="c5c63-111">このガベージ コレクションに関連するすべてのコールバックの間で発生、`GarbageCollectionStarted`コールバックと、対応する[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="c5c63-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="c5c63-112">これらのコールバックは必要があります、同じスレッドでは発生しません。</span><span class="sxs-lookup"><span data-stu-id="c5c63-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="c5c63-113">プロファイラーの中に元の場所にオブジェクトを検査を安全では、`GarbageCollectionStarted`コールバック。</span><span class="sxs-lookup"><span data-stu-id="c5c63-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="c5c63-114">戻り値の後に、ガベージ コレクターがオブジェクト移動を開始`GarbageCollectionStarted`です。</span><span class="sxs-lookup"><span data-stu-id="c5c63-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="c5c63-115">プロファイラーが無効であることを受信するまでのすべてのオブジェクト Id を検討してください、プロファイラーがこのコールバックから返された後、`ICorProfilerCallback2::GarbageCollectionFinished`コールバック。</span><span class="sxs-lookup"><span data-stu-id="c5c63-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c63-116">要件</span><span class="sxs-lookup"><span data-stu-id="c5c63-116">Requirements</span></span>  
 <span data-ttu-id="c5c63-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5c63-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c63-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5c63-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5c63-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5c63-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5c63-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c63-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c63-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5c63-121">See Also</span></span>  
 [<span data-ttu-id="c5c63-122">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5c63-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c5c63-123">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5c63-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
