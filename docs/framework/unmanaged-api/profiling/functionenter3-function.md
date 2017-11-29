---
title: "FunctionEnter3 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter3
helpviewer_keywords: FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08ab1b6adc3d4038a57a187519e96c7a07f1e6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter3-function"></a><span data-ttu-id="0c718-102">FunctionEnter3 関数</span><span class="sxs-lookup"><span data-stu-id="0c718-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="0c718-103">コントロールが関数に渡されることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0c718-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c718-104">構文</span><span class="sxs-lookup"><span data-stu-id="0c718-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c718-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c718-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="0c718-106">[in]制御が渡されます関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="0c718-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c718-107">コメント</span><span class="sxs-lookup"><span data-stu-id="0c718-107">Remarks</span></span>  
 <span data-ttu-id="0c718-108">`FunctionEnter3`関数が呼び出されるが、サポート引数検査されません、コールバック関数がプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0c718-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="0c718-109">使用して、 [icorprofilerinfo 3::setenterleavefunctionhooks3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)をこの関数の実装を登録します。</span><span class="sxs-lookup"><span data-stu-id="0c718-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="0c718-110">`FunctionEnter3`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c718-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="0c718-111">実装を使用する必要があります、`__declspec(naked)`ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="0c718-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="0c718-112">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="0c718-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="0c718-113">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c718-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="0c718-114">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c718-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c718-115">要件</span><span class="sxs-lookup"><span data-stu-id="0c718-115">Requirements</span></span>  
 <span data-ttu-id="0c718-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c718-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c718-117">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="0c718-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0c718-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c718-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c718-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c718-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c718-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c718-120">See Also</span></span>  
 [<span data-ttu-id="0c718-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="0c718-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="0c718-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="0c718-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="0c718-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0c718-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="0c718-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0c718-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="0c718-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0c718-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="0c718-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="0c718-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="0c718-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0c718-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="0c718-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="0c718-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="0c718-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="0c718-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="0c718-130">プロファイリング グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="0c718-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
