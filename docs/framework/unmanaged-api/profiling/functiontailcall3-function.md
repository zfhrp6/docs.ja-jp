---
title: "FunctionTailcall3 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall3
helpviewer_keywords: FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5d274c966a345e0e2984018bcd8aa1e2dade03b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="acb31-102">FunctionTailcall3 関数</span><span class="sxs-lookup"><span data-stu-id="acb31-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="acb31-103">現在実行中の関数は、別の関数の末尾呼び出しを実行しようとして、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="acb31-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb31-104">構文</span><span class="sxs-lookup"><span data-stu-id="acb31-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acb31-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acb31-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="acb31-106">[in]Tail の呼び出しを行うには、現在実行中の関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="acb31-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acb31-107">コメント</span><span class="sxs-lookup"><span data-stu-id="acb31-107">Remarks</span></span>  
 <span data-ttu-id="acb31-108">`FunctionTailcall3`ように関数が呼び出されるコールバック関数がプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="acb31-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="acb31-109">使用して、 [icorprofilerinfo 3::setenterleavefunctionhooks3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)をこの関数の実装を登録します。</span><span class="sxs-lookup"><span data-stu-id="acb31-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="acb31-110">`FunctionTailcall3`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acb31-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="acb31-111">実装を使用する必要があります、`__declspec(naked)`ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="acb31-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="acb31-112">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="acb31-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="acb31-113">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acb31-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="acb31-114">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acb31-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="acb31-115">実装`FunctionTailcall3`をブロックしないでください、ガベージ コレクションが延期されます。</span><span class="sxs-lookup"><span data-stu-id="acb31-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="acb31-116">実装しないでください、ガベージ コレクション スタックはガベージ コレクションに適した状態ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="acb31-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="acb31-117">ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionTailcall3`を返します。</span><span class="sxs-lookup"><span data-stu-id="acb31-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="acb31-118">`FunctionTailcall3`関数がマネージ コードを呼び出していない、または任意の方法で管理されているメモリの割り当てが発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acb31-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb31-119">要件</span><span class="sxs-lookup"><span data-stu-id="acb31-119">Requirements</span></span>  
 <span data-ttu-id="acb31-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="acb31-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb31-121">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="acb31-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="acb31-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acb31-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acb31-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb31-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb31-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="acb31-124">See Also</span></span>  
 [<span data-ttu-id="acb31-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="acb31-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="acb31-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="acb31-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="acb31-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="acb31-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="acb31-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="acb31-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="acb31-129">FunctionTailcall3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="acb31-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="acb31-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="acb31-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="acb31-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="acb31-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="acb31-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="acb31-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="acb31-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="acb31-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="acb31-134">プロファイリング グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="acb31-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
