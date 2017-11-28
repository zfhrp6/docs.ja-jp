---
title: "FunctionTailcall2 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall2
helpviewer_keywords: FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c1f9b0f6a83b774f6b308f7d4daa068eadebcce4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="480f4-102">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="480f4-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="480f4-103">現在実行中の関数は、別の関数の末尾呼び出しを実行する直前と、スタック フレームに関する情報を提供をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="480f4-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="480f4-104">構文</span><span class="sxs-lookup"><span data-stu-id="480f4-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="480f4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="480f4-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="480f4-106">[in]Tail の呼び出しを行うには、現在実行中の関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="480f4-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="480f4-107">[in]使用して、プロファイラーが指定されていたかを再割り当て関数識別子[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)tail の呼び出しを行うには、現在実行中の関数。</span><span class="sxs-lookup"><span data-stu-id="480f4-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="480f4-108">[in]A`COR_PRF_FRAME_INFO`スタック フレームに関する情報を示す値。</span><span class="sxs-lookup"><span data-stu-id="480f4-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="480f4-109">プロファイラーはこれを不透明なハンドルでの実行エンジンに渡すことができるとして扱う必要があります、 [icorprofilerinfo 2::getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="480f4-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="480f4-110">コメント</span><span class="sxs-lookup"><span data-stu-id="480f4-110">Remarks</span></span>  
 <span data-ttu-id="480f4-111">末尾呼び出しの対象の関数は、現在のスタック フレームが使用され、直接 tail の呼び出しを行った関数の呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="480f4-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="480f4-112">つまり、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)末尾呼び出しの対象となっている関数のコールバックは発行されません。</span><span class="sxs-lookup"><span data-stu-id="480f4-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="480f4-113">値、`func`パラメーターが後に無効、`FunctionTailcall2`値が変わる可能性があるか、破棄されるので、返されます。</span><span class="sxs-lookup"><span data-stu-id="480f4-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="480f4-114">`FunctionTailcall2`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="480f4-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="480f4-115">実装を使用する必要があります、 `__declspec`(`naked`) ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="480f4-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="480f4-116">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="480f4-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="480f4-117">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="480f4-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="480f4-118">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="480f4-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="480f4-119">実装`FunctionTailcall2`ガベージ コレクションを遅らせることがあるためにをブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="480f4-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="480f4-120">実装は、ガベージ コレクションをしないでスタックはガベージ コレクションに適した状態ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="480f4-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="480f4-121">ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionTailcall2`を返します。</span><span class="sxs-lookup"><span data-stu-id="480f4-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="480f4-122">また、`FunctionTailcall2`関数を呼び出してはならないようにまたはマネージ コードにマネージ メモリの割り当て。</span><span class="sxs-lookup"><span data-stu-id="480f4-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="480f4-123">要件</span><span class="sxs-lookup"><span data-stu-id="480f4-123">Requirements</span></span>  
 <span data-ttu-id="480f4-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="480f4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="480f4-125">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="480f4-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="480f4-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="480f4-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="480f4-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="480f4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="480f4-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="480f4-128">See Also</span></span>  
 [<span data-ttu-id="480f4-129">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="480f4-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="480f4-130">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="480f4-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="480f4-131">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="480f4-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="480f4-132">プロファイリング グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="480f4-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
