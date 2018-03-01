---
title: "FunctionLeave2 関数"
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
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86ffb6cc18de0b0b7b68b418477c1e8cdd6e6cc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="functionleave2-function"></a><span data-ttu-id="78072-102">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="78072-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="78072-103">プロファイラーに通知関数が呼び出し元に戻るには、し、スタック フレームと関数の戻り値に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="78072-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78072-104">構文</span><span class="sxs-lookup"><span data-stu-id="78072-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78072-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78072-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="78072-106">[in]返す関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="78072-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="78072-107">[in]使用して、プロファイラーが指定されていた再マップされた関数の識別子、 [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="78072-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="78072-108">[in]A`COR_PRF_FRAME_INFO`スタック フレームに関する情報を示す値。</span><span class="sxs-lookup"><span data-stu-id="78072-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="78072-109">プロファイラーはこれを不透明なハンドルでの実行エンジンに渡すことができるとして扱う必要があります、 [icorprofilerinfo 2::getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="78072-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="78072-110">[in]ポインター、 [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)を関数の戻り値のメモリ位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="78072-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="78072-111">戻り値の情報にアクセスするために、`COR_PRF_ENABLE_FUNCTION_RETVAL`フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78072-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="78072-112">プロファイラーは、使用、 [icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベント フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="78072-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78072-113">コメント</span><span class="sxs-lookup"><span data-stu-id="78072-113">Remarks</span></span>  
 <span data-ttu-id="78072-114">値、`func`と`retvalRange`パラメーターが後に無効、`FunctionLeave2`値は変更または破棄されるので、返されます。</span><span class="sxs-lookup"><span data-stu-id="78072-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="78072-115">`FunctionLeave2`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78072-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="78072-116">実装を使用する必要があります、 `__declspec`(`naked`) ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="78072-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="78072-117">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="78072-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="78072-118">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78072-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="78072-119">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78072-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="78072-120">実装`FunctionLeave2`ガベージ コレクションを遅らせることがあるためにをブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="78072-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="78072-121">実装は、ガベージ コレクションをしないでスタックはガベージ コレクションに適した状態ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="78072-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="78072-122">ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionLeave2`を返します。</span><span class="sxs-lookup"><span data-stu-id="78072-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="78072-123">また、`FunctionLeave2`関数を呼び出してはならないようにまたはマネージ コードにマネージ メモリの割り当て。</span><span class="sxs-lookup"><span data-stu-id="78072-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78072-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="78072-124">Requirements</span></span>  
 <span data-ttu-id="78072-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78072-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78072-126">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="78072-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="78072-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78072-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78072-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78072-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78072-129">参照</span><span class="sxs-lookup"><span data-stu-id="78072-129">See Also</span></span>  
 [<span data-ttu-id="78072-130">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="78072-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="78072-131">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="78072-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="78072-132">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="78072-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="78072-133">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="78072-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
