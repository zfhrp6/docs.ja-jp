---
title: "ICorProfilerCallback::ObjectReferences メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30b8f6b5f424ff81ace36baa8d2ae39e0a2f1d1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="b5435-102">ICorProfilerCallback::ObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="b5435-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="b5435-103">指定したオブジェクトによって参照されているメモリ内のオブジェクトをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b5435-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5435-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5435-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5435-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5435-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b5435-106">[in]オブジェクトを参照しているオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="b5435-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="b5435-107">[in]クラスのインスタンスでは、指定したオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="b5435-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="b5435-108">[in]指定したオブジェクトによって参照されるオブジェクトの数 (つまり、内の要素の数、`objectRefIds`配列)。</span><span class="sxs-lookup"><span data-stu-id="b5435-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="b5435-109">[in]によって参照されているオブジェクトの Id の配列`objectId`です。</span><span class="sxs-lookup"><span data-stu-id="b5435-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5435-110">コメント</span><span class="sxs-lookup"><span data-stu-id="b5435-110">Remarks</span></span>  
 <span data-ttu-id="b5435-111">`ObjectReferences`ガベージ コレクションが完了した後に、ヒープの残りの各オブジェクトのメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b5435-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="b5435-112">プロファイラーでは、このコールバックからエラーが返された場合をプロファイリング サービスは次のガベージ コレクションまでこのコールバックの呼び出しを中止します。</span><span class="sxs-lookup"><span data-stu-id="b5435-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="b5435-113">`ObjectReferences`コールバックを組み合わせて使用することができます、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)ランタイムの完全なオブジェクト参照グラフを作成するコールバック。</span><span class="sxs-lookup"><span data-stu-id="b5435-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="b5435-114">共通言語ランタイム (CLR) により、それぞれのオブジェクト参照をによって一度だけ報告、`ObjectReferences`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b5435-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="b5435-115">によって返されるオブジェクト Id`ObjectReferences`自体には、コールバック中に無効なため、オブジェクトを移動中にガベージ コレクションがある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b5435-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="b5435-116">そのため、プロファイラーは、中にオブジェクトを検査する試みる必要がありますいない、`ObjectReferences`呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b5435-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="b5435-117">ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、ガベージ コレクションが完了し、検査を安全に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b5435-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="b5435-118">Null`ClassId`ことを示します`objectId`型がアンロード中が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b5435-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5435-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="b5435-119">Requirements</span></span>  
 <span data-ttu-id="b5435-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5435-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5435-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5435-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5435-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5435-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5435-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5435-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5435-124">参照</span><span class="sxs-lookup"><span data-stu-id="b5435-124">See Also</span></span>  
 [<span data-ttu-id="b5435-125">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5435-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
