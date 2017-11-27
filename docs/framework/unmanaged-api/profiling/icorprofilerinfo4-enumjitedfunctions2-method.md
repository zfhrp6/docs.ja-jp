---
title: "ICorProfilerInfo4::EnumJITedFunctions2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumJITedFunctions2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9b9c8739a8ab47b4e24dba1b15c228d2800290d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="9e579-102">ICorProfilerInfo4::EnumJITedFunctions2 メソッド</span><span class="sxs-lookup"><span data-stu-id="9e579-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="9e579-103">以前に JIT コンパイルされ、JIT 再コンパイルしていたすべての関数の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="9e579-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="9e579-104">このメソッドは、置換、 [icorprofilerinfo 3::enumjitedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)メソッドの JIT 再コンパイルの Id を列挙できません。</span><span class="sxs-lookup"><span data-stu-id="9e579-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e579-105">構文</span><span class="sxs-lookup"><span data-stu-id="9e579-105">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e579-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9e579-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9e579-107">[out]ポインター、 [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)列挙子。</span><span class="sxs-lookup"><span data-stu-id="9e579-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e579-108">コメント</span><span class="sxs-lookup"><span data-stu-id="9e579-108">Remarks</span></span>  
 <span data-ttu-id="9e579-109">このメソッドと重なる可能性があります`JITCompilation`など、コールバック、 [icorprofilercallback::jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9e579-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="9e579-110">返される列挙体には値が含まれています、`COR_PRF_FUNCTION::reJitId`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="9e579-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="9e579-111">[Icorprofilerinfo 3::enumjitedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)ためこのメソッドに代わる、メソッドが JIT 再コンパイルの Id を列挙できません、`COR_PRF_FUNCTION::reJitId`フィールドは常に 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="9e579-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="9e579-112">`ICorProfilerInfo4::EnumJITedFunctions`のためにメソッドが JIT 再コンパイルの Id を列挙は、`COR_PRF_FUNCTION::reJitId`フィールドが適切に設定します。</span><span class="sxs-lookup"><span data-stu-id="9e579-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="9e579-113">なお、 [icorprofilerinfo 4::enumjitedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)一方、メソッドは、ガベージ コレクションをトリガーできます[icorprofilerinfo 3::enumjitedfunctions メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)は表示されません。</span><span class="sxs-lookup"><span data-stu-id="9e579-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="9e579-114">詳細については、次を参照してください。 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e579-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e579-115">要件</span><span class="sxs-lookup"><span data-stu-id="9e579-115">Requirements</span></span>  
 <span data-ttu-id="9e579-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e579-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e579-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e579-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e579-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e579-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e579-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e579-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e579-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e579-120">See Also</span></span>  
 [<span data-ttu-id="9e579-121">EnumJITedFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="9e579-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)  
 [<span data-ttu-id="9e579-122">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e579-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="9e579-123">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e579-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9e579-124">プロファイル</span><span class="sxs-lookup"><span data-stu-id="9e579-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
