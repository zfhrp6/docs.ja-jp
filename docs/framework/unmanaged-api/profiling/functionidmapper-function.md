---
title: "FunctionIDMapper 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper
helpviewer_keywords: FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24e48ecb551a5faacc7da94b857b2e260f5aeca0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="functionidmapper-function"></a><span data-ttu-id="020b8-102">FunctionIDMapper 関数</span><span class="sxs-lookup"><span data-stu-id="020b8-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="020b8-103">関数の特定の識別子が可能性がありますで使用される代替 ID に再割り当てされることをプロファイラーに通知、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)、および[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)その関数のコールバック。</span><span class="sxs-lookup"><span data-stu-id="020b8-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="020b8-104">また `FunctionIDMapper` により、プロファイラーはその関数のコールバックを受信するかどうかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="020b8-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="020b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="020b8-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="020b8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="020b8-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="020b8-107">[入力] 再割り当てされる関数識別子。</span><span class="sxs-lookup"><span data-stu-id="020b8-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="020b8-108">[out]プロファイラーに設定される値へのポインター`true`を受信する必要がある場合`FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`コールバックです。 それ以外の場合この値が設定`false`です。</span><span class="sxs-lookup"><span data-stu-id="020b8-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="020b8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="020b8-109">Return Value</span></span>  
 <span data-ttu-id="020b8-110">プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。</span><span class="sxs-lookup"><span data-stu-id="020b8-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="020b8-111">`false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="020b8-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="020b8-112">それ以外の場合、戻り値を null、プロセスの中止など、予期しない結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="020b8-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="020b8-113">コメント</span><span class="sxs-lookup"><span data-stu-id="020b8-113">Remarks</span></span>  
 <span data-ttu-id="020b8-114">`FunctionIDMapper`関数がコールバック。</span><span class="sxs-lookup"><span data-stu-id="020b8-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="020b8-115">プロファイラーのより有用なは、他の何らかの識別子に関数の ID を再マップするには、プロファイラーによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="020b8-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="020b8-116">`FunctionIDMapper`任意指定の関数に使用される代替 ID を返します。</span><span class="sxs-lookup"><span data-stu-id="020b8-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="020b8-117">実行エンジンは、し、適用することで、プロファイラーの要求だけでなく、従来の関数の ID では、この別の ID でプロファイラーに渡すことによって、`clientData`のパラメーター、 `FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`フックを識別するには対象のフック関数が呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="020b8-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="020b8-118">使用することができます、 [icorprofilerinfo::setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)メソッドの実装を指定する、`FunctionIDMapper`関数。</span><span class="sxs-lookup"><span data-stu-id="020b8-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="020b8-119">呼び出すことができます、`ICorProfilerInfo::SetFunctionIDMapper`とメソッドを 1 回のみに実行することをお勧め、 [icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="020b8-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="020b8-120">既定と見なされますこと、プロファイラーを COR_PRF_MONITOR_ENTERLEAVE フラグ設定を使用して[icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)を使用してフックを設定して[icorprofilerinfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)または[icorprofilerinfo 2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)、受信する必要があります、 `FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`関数は、すべてのコールバック。</span><span class="sxs-lookup"><span data-stu-id="020b8-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="020b8-121">ただし、プロファイラーの実装が`FunctionIDMapper`選択的に受信しないためにこれらのコールバック特定の設定によって機能`pbHookFunction`に`false`です。</span><span class="sxs-lookup"><span data-stu-id="020b8-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="020b8-122">プロファイラーは、プロファイリング対象のアプリケーションの複数のスレッドが、同じメソッド/関数を同時に呼び出す場合に対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="020b8-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="020b8-123">このような場合、プロファイラーが表示される複数`FunctionIDMapper`のコールバックを同じ`FunctionID`です。</span><span class="sxs-lookup"><span data-stu-id="020b8-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="020b8-124">プロファイラーがする必要がありますが同じ複数回呼び出された場合、このコールバックから同じの値を返す特定`FunctionID`です。</span><span class="sxs-lookup"><span data-stu-id="020b8-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="020b8-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="020b8-125">Requirements</span></span>  
 <span data-ttu-id="020b8-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="020b8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="020b8-127">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="020b8-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="020b8-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="020b8-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="020b8-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="020b8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020b8-130">参照</span><span class="sxs-lookup"><span data-stu-id="020b8-130">See Also</span></span>  
 [<span data-ttu-id="020b8-131">SetFunctionIDMapper メソッド</span><span class="sxs-lookup"><span data-stu-id="020b8-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="020b8-132">FunctionIDMapper2 関数</span><span class="sxs-lookup"><span data-stu-id="020b8-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [<span data-ttu-id="020b8-133">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="020b8-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="020b8-134">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="020b8-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="020b8-135">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="020b8-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="020b8-136">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="020b8-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
