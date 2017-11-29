---
title: "FunctionLeave3WithInfo 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave3WithInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave3WithInfo
helpviewer_keywords: FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e42614531afb11a811e8862abad0caddf8873483
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="c18ff-102">FunctionLeave3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="c18ff-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="c18ff-103">コントロールが、関数から返されていることをプロファイラーに通知しに渡すことができるハンドルを提供、 [icorprofilerinfo 3::getfunctionleave3info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)スタック フレームおよび戻り値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c18ff-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="c18ff-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c18ff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c18ff-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="c18ff-106">[in]制御が返される関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="c18ff-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="c18ff-107">[in] 特定のスタック フレームに関する情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="c18ff-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="c18ff-108">このハンドルは、渡されるコールバック中にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="c18ff-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c18ff-109">コメント</span><span class="sxs-lookup"><span data-stu-id="c18ff-109">Remarks</span></span>  
 <span data-ttu-id="c18ff-110">`FunctionLeave3WithInfo`関数が呼び出され、により、プロファイラーを使用すると、プロファイラーに通知のコールバック メソッド、 [icorprofilerinfo 3::getfunctionleave3info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)を戻り値を検査します。</span><span class="sxs-lookup"><span data-stu-id="c18ff-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="c18ff-111">戻り値の情報にアクセスする、`COR_PRF_ENABLE_FUNCTION_RETVAL`を設定するフラグを持っています。</span><span class="sxs-lookup"><span data-stu-id="c18ff-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="c18ff-112">プロファイラーは、使用、 [icorprofilerinfo::seteventmask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベント フラグを設定し、使用して、 [icorprofilerinfo 3::setenterleavefunctionhooks3withinfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)を登録する、この関数の実装です。</span><span class="sxs-lookup"><span data-stu-id="c18ff-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="c18ff-113">`FunctionLeave3WithInfo`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c18ff-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="c18ff-114">実装を使用する必要があります、`__declspec(naked)`ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="c18ff-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="c18ff-115">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="c18ff-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="c18ff-116">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c18ff-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="c18ff-117">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c18ff-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c18ff-118">実装`FunctionLeave3WithInfo`をブロックしないでください、ガベージ コレクションが延期されます。</span><span class="sxs-lookup"><span data-stu-id="c18ff-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="c18ff-119">実装しないでください、ガベージ コレクション スタックはガベージ コレクションに適した状態ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c18ff-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c18ff-120">ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionLeave3WithInfo`を返します。</span><span class="sxs-lookup"><span data-stu-id="c18ff-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="c18ff-121">`FunctionLeave3WithInfo`関数がマネージ コードを呼び出していない、または任意の方法で管理されているメモリの割り当てが発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c18ff-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c18ff-122">要件</span><span class="sxs-lookup"><span data-stu-id="c18ff-122">Requirements</span></span>  
 <span data-ttu-id="c18ff-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c18ff-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c18ff-124">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c18ff-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c18ff-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c18ff-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c18ff-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c18ff-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c18ff-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c18ff-127">See Also</span></span>  
 [<span data-ttu-id="c18ff-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="c18ff-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)  
 [<span data-ttu-id="c18ff-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="c18ff-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="c18ff-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="c18ff-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="c18ff-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="c18ff-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="c18ff-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c18ff-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="c18ff-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c18ff-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="c18ff-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="c18ff-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="c18ff-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c18ff-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="c18ff-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="c18ff-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="c18ff-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="c18ff-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="c18ff-138">プロファイリング グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="c18ff-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
