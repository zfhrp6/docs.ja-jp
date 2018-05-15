---
title: ICorProfilerInfo2::GetGenerationBounds メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cfac1304a3d60a418065e4fc2994705548eeac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="45cd7-102">ICorProfilerInfo2::GetGenerationBounds メソッド</span><span class="sxs-lookup"><span data-stu-id="45cd7-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="45cd7-103">各種ガベージ コレクション ジェネレーションを構成するメモリ領域 (ヒープのセグメント) を取得します。</span><span class="sxs-lookup"><span data-stu-id="45cd7-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cd7-104">構文</span><span class="sxs-lookup"><span data-stu-id="45cd7-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45cd7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="45cd7-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="45cd7-106">[in] `ranges` 配列の呼び出し元によって割り当てられた要素の数。</span><span class="sxs-lookup"><span data-stu-id="45cd7-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="45cd7-107">[out] その一部または全部が `ranges` 配列で返される範囲の総数を指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="45cd7-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="45cd7-108">[out]配列[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)構造体、ガベージ コレクションが実行しているジェネレーション内のメモリ範囲 (ブロック) それぞれについて説明します。</span><span class="sxs-lookup"><span data-stu-id="45cd7-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45cd7-109">コメント</span><span class="sxs-lookup"><span data-stu-id="45cd7-109">Remarks</span></span>  
 <span data-ttu-id="45cd7-110">ガベージ コレクションを処理中でない場合、`GetGenerationBounds` メソッドは任意のプロファイラー コールバックから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="45cd7-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="45cd7-111">つまり、間に発生するものを除く任意のコールバックから呼び出すことがあります[icorprofilercallback 2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)と[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="45cd7-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="45cd7-112">通常、ジェネレーションの移動はガベージ コレクション中に行われます。</span><span class="sxs-lookup"><span data-stu-id="45cd7-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="45cd7-113">コレクションの間にジェネレーションが増大する可能性はありますが、一般的に移動はありません。</span><span class="sxs-lookup"><span data-stu-id="45cd7-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="45cd7-114">したがって、`GetGenerationBounds` を呼び出す上で最も注目すべき地点は `ICorProfilerCallback2::GarbageCollectionStarted` と `ICorProfilerCallback2::GarbageCollectionFinished` の間です。</span><span class="sxs-lookup"><span data-stu-id="45cd7-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="45cd7-115">プログラムの起動中に、いくつかのオブジェクトが共通言語ランタイム (CLR) 自体によって割り当てられます。これは、一般的にはジェネレーションの 3 と 0 で行われます。</span><span class="sxs-lookup"><span data-stu-id="45cd7-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="45cd7-116">したがって、マネージ コードが実行を開始するまでに、これらのジェネレーションには既にオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="45cd7-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="45cd7-117">通常、ジェネレーションの 1 と 2 は、ガベージ コレクターによって生成されたダミー オブジェクトを除き、空です。</span><span class="sxs-lookup"><span data-stu-id="45cd7-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="45cd7-118">(ダミー オブジェクトのサイズは、CLR の 32 ビット実装で 12 バイト、64 ビット実装ではそれよりも大きくなります。)ジェネレーション 2 の範囲がネイティブ イメージ ジェネレーター (NGen.exe) によって作成されたモジュール内のこともあります。</span><span class="sxs-lookup"><span data-stu-id="45cd7-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="45cd7-119">ここでは、ジェネレーション 2 のオブジェクトは*固定オブジェクト*、ガベージ コレクターではなく、NGen.exe 実行時にこれが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="45cd7-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="45cd7-120">この関数は、呼び出し元が割り当てたバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="45cd7-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45cd7-121">要件</span><span class="sxs-lookup"><span data-stu-id="45cd7-121">Requirements</span></span>  
 <span data-ttu-id="45cd7-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="45cd7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45cd7-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45cd7-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45cd7-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45cd7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45cd7-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45cd7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cd7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="45cd7-126">See Also</span></span>  
 [<span data-ttu-id="45cd7-127">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45cd7-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="45cd7-128">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45cd7-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="45cd7-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="45cd7-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="45cd7-130">プロファイル</span><span class="sxs-lookup"><span data-stu-id="45cd7-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
