---
title: "FunctionEnter3WithInfo 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3WithInfo
api_location: mscorwks.cll
api_type: COM
f1_keywords: FunctionEnter3WithInfo
helpviewer_keywords: FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 848ef06f73aa0cce5d6991a7a59a8ce51ab1745a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="2c2e1-102">FunctionEnter3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="2c2e1-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="2c2e1-103">コントロールが、関数に渡されることをプロファイラーに通知しに渡すことができるハンドルを提供、 [icorprofilerinfo 3::getfunctionenter3info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)スタック フレームと関数の引数を取得します。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c2e1-104">構文</span><span class="sxs-lookup"><span data-stu-id="2c2e1-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c2e1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c2e1-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="2c2e1-106">[in]制御が渡されます関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="2c2e1-107">[in] 特定のスタック フレームに関する情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="2c2e1-108">このハンドルは、渡されるコールバック中にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c2e1-109">コメント</span><span class="sxs-lookup"><span data-stu-id="2c2e1-109">Remarks</span></span>  
 <span data-ttu-id="2c2e1-110">`FunctionEnter3WithInfo`関数が呼び出され、により、プロファイラーを使用すると、プロファイラーに通知のコールバック メソッド、 [icorprofilerinfo 3::getfunctionenter3info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)を引数の値を検査します。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="2c2e1-111">引数の情報にアクセスする、`COR_PRF_ENABLE_FUNCTION_ARGS`を設定するフラグを持っています。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="2c2e1-112">プロファイラーは、使用、 [icorprofilerinfo::seteventmask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベント フラグを設定し、使用して、 [icorprofilerinfo 3::setenterleavefunctionhooks3withinfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)を登録する、この関数の実装です。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="2c2e1-113">`FunctionEnter3WithInfo`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="2c2e1-114">実装を使用する必要があります、`__declspec(naked)`ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="2c2e1-115">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="2c2e1-116">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="2c2e1-117">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="2c2e1-118">実装`FunctionEnter3WithInfo`をブロックしないでください、ガベージ コレクションが延期されます。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="2c2e1-119">実装しないでください、ガベージ コレクション スタックはガベージ コレクションに適した状態ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="2c2e1-120">ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionEnter3WithInfo`を返します。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="2c2e1-121">`FunctionEnter3WithInfo`関数がマネージ コードを呼び出していない、または任意の方法で管理されているメモリの割り当てが発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c2e1-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="2c2e1-122">Requirements</span></span>  
 <span data-ttu-id="2c2e1-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2c2e1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c2e1-124">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="2c2e1-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2c2e1-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c2e1-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c2e1-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c2e1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2e1-127">参照</span><span class="sxs-lookup"><span data-stu-id="2c2e1-127">See Also</span></span>  
 [<span data-ttu-id="2c2e1-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="2c2e1-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [<span data-ttu-id="2c2e1-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="2c2e1-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="2c2e1-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="2c2e1-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="2c2e1-131">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="2c2e1-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
