---
title: "ICorProfilerInfo4::GetReJITIDs メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetReJITIDs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc16cd932fc2ce0cf5cb53c227081501e79ed2d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="f3dbe-102">ICorProfilerInfo4::GetReJITIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="f3dbe-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="f3dbe-103">JIT 再コンパイルのすべてのバージョン指定の関数はまだ割り当てられていることを識別する Id の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="f3dbe-104">これには、後で元に戻されていて (たとえば、元に戻された関数が含まれるアプリケーション ドメインでは、使用されている) ときに解放されていない関数の JIT 再コンパイル バージョンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3dbe-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3dbe-105">Syntax</span></span>  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3dbe-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3dbe-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f3dbe-107">[in]`FunctionID`関数のインスタンスのバージョンを列挙するのです。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="f3dbe-108">[in]割り当てられた JIT 再コンパイルの Id の数、`reJitIds`配列。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="f3dbe-109">[out]実際の Id の JIT 再コンパイルの数。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="f3dbe-110">[out]指定した関数の JIT 再コンパイルの Id を格納する、呼び出し元が割り当てた配列。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3dbe-111">コメント</span><span class="sxs-lookup"><span data-stu-id="f3dbe-111">Remarks</span></span>  
 <span data-ttu-id="f3dbe-112">`GetReJITIDs`指定された関数のインスタンスの JIT 再コンパイルのアクティブな Id を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="f3dbe-113">その他の同様の使用状況パターンが続く`ICorProfilerInfo`呼び出し元が割り当てたバッファーを受け取る関数をします。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3dbe-114">要件</span><span class="sxs-lookup"><span data-stu-id="f3dbe-114">Requirements</span></span>  
 <span data-ttu-id="f3dbe-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3dbe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3dbe-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3dbe-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3dbe-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3dbe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3dbe-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3dbe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dbe-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3dbe-119">See Also</span></span>  
 [<span data-ttu-id="f3dbe-120">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3dbe-120">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="f3dbe-121">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3dbe-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f3dbe-122">プロファイル</span><span class="sxs-lookup"><span data-stu-id="f3dbe-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
