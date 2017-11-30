---
title: "ICorProfilerInfo2::GetObjectGeneration メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetObjectGeneration
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e90139f96638dbb1a183f98e754838ff52424fc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="62ca3-102">ICorProfilerInfo2::GetObjectGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="62ca3-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="62ca3-103">指定したオブジェクトを含むヒープのセグメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="62ca3-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ca3-104">構文</span><span class="sxs-lookup"><span data-stu-id="62ca3-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62ca3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62ca3-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="62ca3-106">[in]オブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="62ca3-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="62ca3-107">[out]ポインター、 [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)構造体は、ガベージ コレクションが実行しているジェネレーション内のメモリ範囲 (ブロック) を記述します。</span><span class="sxs-lookup"><span data-stu-id="62ca3-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="62ca3-108">この範囲には、指定したオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="62ca3-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62ca3-109">コメント</span><span class="sxs-lookup"><span data-stu-id="62ca3-109">Remarks</span></span>  
 <span data-ttu-id="62ca3-110">`GetObjectGeneration`ガベージ コレクションが実行されていないこと、任意のプロファイラー コールバックからメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="62ca3-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="62ca3-111">つまり、間に発生するものを除く任意のコールバックから呼び出すことがあります[icorprofilercallback 2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)と[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="62ca3-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ca3-112">要件</span><span class="sxs-lookup"><span data-stu-id="62ca3-112">Requirements</span></span>  
 <span data-ttu-id="62ca3-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="62ca3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ca3-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62ca3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62ca3-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62ca3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62ca3-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ca3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ca3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="62ca3-117">See Also</span></span>  
 [<span data-ttu-id="62ca3-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62ca3-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="62ca3-119">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62ca3-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)