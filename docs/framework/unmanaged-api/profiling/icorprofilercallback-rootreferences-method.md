---
title: "ICorProfilerCallback::RootReferences メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RootReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a12dec1ed0fecad235090592def9689f60e50193
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="673cd-102">ICorProfilerCallback::RootReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="673cd-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="673cd-103">ガベージ コレクション後のルート参照に関する情報をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="673cd-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="673cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="673cd-104">Syntax</span></span>  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="673cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="673cd-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="673cd-106">[in]参照の数、`rootRefIds`配列。</span><span class="sxs-lookup"><span data-stu-id="673cd-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="673cd-107">[in]静的オブジェクトまたはスタック上のオブジェクトのいずれかを参照するオブジェクト Id の配列。</span><span class="sxs-lookup"><span data-stu-id="673cd-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="673cd-108">コメント</span><span class="sxs-lookup"><span data-stu-id="673cd-108">Remarks</span></span>  
 <span data-ttu-id="673cd-109">両方`RootReferences`と[icorprofilercallback 2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)をプロファイラーに通知と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="673cd-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="673cd-110">プロファイラーは、どちらか一方、実装通常しますが、どちらの情報が渡されるため`RootReferences2`に渡されたのスーパー セット`RootReferences`です。</span><span class="sxs-lookup"><span data-stu-id="673cd-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="673cd-111">可能であれば、 `rootRefIds` null オブジェクトを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="673cd-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="673cd-112">たとえば、スタックで宣言されているすべてのオブジェクト参照は、ガベージ コレクターによってルートとして扱われは常に報告されます。</span><span class="sxs-lookup"><span data-stu-id="673cd-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="673cd-113">によって返されるオブジェクト Id`RootReferences`自体には、コールバック中に無効なため古いアドレスから新しいアドレスにオブジェクトを移動中にガベージ コレクションがある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="673cd-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="673cd-114">そのため、プロファイラーは、中にオブジェクトを検査する試みる必要がありますいないを`RootReferences`呼び出します。</span><span class="sxs-lookup"><span data-stu-id="673cd-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="673cd-115">ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、すべてのオブジェクトの新しい場所に移動されましたし、安全に検査することができます。</span><span class="sxs-lookup"><span data-stu-id="673cd-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="673cd-116">要件</span><span class="sxs-lookup"><span data-stu-id="673cd-116">Requirements</span></span>  
 <span data-ttu-id="673cd-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="673cd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="673cd-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="673cd-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="673cd-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="673cd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="673cd-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="673cd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673cd-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="673cd-121">See Also</span></span>  
 [<span data-ttu-id="673cd-122">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="673cd-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
