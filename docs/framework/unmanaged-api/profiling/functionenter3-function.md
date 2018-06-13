---
title: FunctionEnter3 関数
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 466b90f814d267fb289b2804beccd58fc442e341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451881"
---
# <a name="functionenter3-function"></a><span data-ttu-id="b06cb-102">FunctionEnter3 関数</span><span class="sxs-lookup"><span data-stu-id="b06cb-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="b06cb-103">コントロールが関数に渡されることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b06cb-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b06cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="b06cb-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b06cb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b06cb-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="b06cb-106">[in]制御が渡されます関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="b06cb-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b06cb-107">コメント</span><span class="sxs-lookup"><span data-stu-id="b06cb-107">Remarks</span></span>  
 <span data-ttu-id="b06cb-108">`FunctionEnter3`関数が呼び出されるが、サポート引数検査されません、コールバック関数がプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b06cb-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="b06cb-109">使用して、 [icorprofilerinfo 3::setenterleavefunctionhooks3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)をこの関数の実装を登録します。</span><span class="sxs-lookup"><span data-stu-id="b06cb-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="b06cb-110">`FunctionEnter3`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b06cb-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="b06cb-111">実装を使用する必要があります、`__declspec(naked)`ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="b06cb-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="b06cb-112">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="b06cb-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="b06cb-113">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b06cb-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="b06cb-114">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b06cb-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b06cb-115">要件</span><span class="sxs-lookup"><span data-stu-id="b06cb-115">Requirements</span></span>  
 <span data-ttu-id="b06cb-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b06cb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b06cb-117">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b06cb-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b06cb-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b06cb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b06cb-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b06cb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06cb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b06cb-120">See Also</span></span>  
 [<span data-ttu-id="b06cb-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="b06cb-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="b06cb-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="b06cb-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="b06cb-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b06cb-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="b06cb-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b06cb-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="b06cb-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b06cb-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="b06cb-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="b06cb-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="b06cb-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b06cb-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="b06cb-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="b06cb-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="b06cb-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="b06cb-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="b06cb-130">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="b06cb-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
