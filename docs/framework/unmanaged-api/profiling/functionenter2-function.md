---
title: "FunctionEnter2 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter2
helpviewer_keywords: FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0709d54589b3f88b461adde3f3d380407d263855
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter2-function"></a><span data-ttu-id="08c38-102">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="08c38-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="08c38-103">コントロールが関数に渡されると、フレームと関数の引数の履歴に関する情報を提供をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="08c38-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="08c38-104">この関数は、 [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="08c38-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c38-105">構文</span><span class="sxs-lookup"><span data-stu-id="08c38-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08c38-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="08c38-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="08c38-107">[in]制御が渡されます関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="08c38-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="08c38-108">[in]プロファイラーを使用して以前に指定した再マップされた関数の識別子、 [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="08c38-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="08c38-109">[in]A`COR_PRF_FRAME_INFO`スタック フレームに関する情報を示す値。</span><span class="sxs-lookup"><span data-stu-id="08c38-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="08c38-110">プロファイラーはこれを不透明なハンドルでの実行エンジンに渡すことができるとして扱う必要があります、 [icorprofilerinfo 2::getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="08c38-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="08c38-111">[in]ポインター、 [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)を関数の引数のメモリ内の場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="08c38-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="08c38-112">引数の情報にアクセスするために、`COR_PRF_ENABLE_FUNCTION_ARGS`フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08c38-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="08c38-113">プロファイラーは、使用、 [icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベント フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="08c38-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08c38-114">コメント</span><span class="sxs-lookup"><span data-stu-id="08c38-114">Remarks</span></span>  
 <span data-ttu-id="08c38-115">値、`func`と`argumentInfo`パラメーターが後に無効、`FunctionEnter2`値は変更または破棄されるので、返されます。</span><span class="sxs-lookup"><span data-stu-id="08c38-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="08c38-116">`FunctionEnter2`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08c38-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="08c38-117">実装を使用する必要があります、 `__declspec`(`naked`) ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="08c38-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="08c38-118">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="08c38-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="08c38-119">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08c38-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="08c38-120">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08c38-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="08c38-121">実装`FunctionEnter2`ガベージ コレクションを遅らせることがあるためにをブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="08c38-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="08c38-122">実装は、ガベージ コレクションをしないでスタックはガベージ コレクションに適した状態ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="08c38-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="08c38-123">ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionEnter2`を返します。</span><span class="sxs-lookup"><span data-stu-id="08c38-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="08c38-124">また、`FunctionEnter2`関数を呼び出してはならないようにまたはマネージ コードにマネージ メモリの割り当て。</span><span class="sxs-lookup"><span data-stu-id="08c38-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08c38-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="08c38-125">Requirements</span></span>  
 <span data-ttu-id="08c38-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="08c38-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08c38-127">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="08c38-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="08c38-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08c38-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08c38-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08c38-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c38-130">参照</span><span class="sxs-lookup"><span data-stu-id="08c38-130">See Also</span></span>  
 [<span data-ttu-id="08c38-131">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="08c38-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="08c38-132">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="08c38-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="08c38-133">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="08c38-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="08c38-134">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="08c38-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
