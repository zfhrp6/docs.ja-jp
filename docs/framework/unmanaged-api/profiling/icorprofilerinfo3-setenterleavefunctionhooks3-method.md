---
title: "ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 メソッド"
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
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77a2e8170cd2cf78576b2d376fb592c903bbb403
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="be25a-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 メソッド</span><span class="sxs-lookup"><span data-stu-id="be25a-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="be25a-103">呼び出されるプロファイラー実装関数を指定します、 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)、および[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="be25a-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be25a-104">構文</span><span class="sxs-lookup"><span data-stu-id="be25a-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be25a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be25a-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="be25a-106">[in]として使用する実装へのポインター、`FunctionEnter3`コールバック。</span><span class="sxs-lookup"><span data-stu-id="be25a-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="be25a-107">[in]として使用する実装へのポインター、`FunctionLeave3`コールバック。</span><span class="sxs-lookup"><span data-stu-id="be25a-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="be25a-108">[in]として使用する実装へのポインター、`FunctionTailcall3`コールバック。</span><span class="sxs-lookup"><span data-stu-id="be25a-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be25a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="be25a-109">Remarks</span></span>  
 <span data-ttu-id="be25a-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)、および[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)フック スタック フレームおよび引数の検査に渡さないようにします。</span><span class="sxs-lookup"><span data-stu-id="be25a-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="be25a-111">その情報にアクセスする、 `COR_PRF_ENABLE_FUNCTION_ARGS`、 `COR_PRF_ENABLE_FUNCTION_RETVAL`、や`COR_PRF_ENABLE_FRAME_INFO`フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be25a-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="be25a-112">プロファイラーは、使用、 [icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベント フラグを設定して、使用するメソッド、 [icorprofilerinfo 3::setenterleavefunctionhooks3withinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)を登録する方法、この関数の実装です。</span><span class="sxs-lookup"><span data-stu-id="be25a-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="be25a-113">コールバックの 1 つだけのセットは、一度にアクティブにでき、最新バージョンが優先されます。</span><span class="sxs-lookup"><span data-stu-id="be25a-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="be25a-114">そのため、プロファイラーは、両方を呼び出す場合、 [SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)と`SetEnterLeaveFunctionHooks3`メソッド、`SetEnterLeaveFunctionHooks3`を使用します。</span><span class="sxs-lookup"><span data-stu-id="be25a-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="be25a-115">`SetEnterLeaveFunctionHooks3`メソッドは、プロファイラーからのみ呼び出すことがあります[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="be25a-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be25a-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="be25a-116">Requirements</span></span>  
 <span data-ttu-id="be25a-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="be25a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be25a-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be25a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be25a-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be25a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be25a-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be25a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be25a-121">参照</span><span class="sxs-lookup"><span data-stu-id="be25a-121">See Also</span></span>  
 [<span data-ttu-id="be25a-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="be25a-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="be25a-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="be25a-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="be25a-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="be25a-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="be25a-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="be25a-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="be25a-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="be25a-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="be25a-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="be25a-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="be25a-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="be25a-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="be25a-129">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="be25a-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="be25a-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="be25a-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="be25a-131">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="be25a-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="be25a-132">プロファイル</span><span class="sxs-lookup"><span data-stu-id="be25a-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
