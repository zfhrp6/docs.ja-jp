---
title: "FunctionEnter 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter
helpviewer_keywords: FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd98e6db0f400d022fe0af4e96336616cbb7183
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter-function"></a><span data-ttu-id="e6b64-102">FunctionEnter 関数</span><span class="sxs-lookup"><span data-stu-id="e6b64-102">FunctionEnter Function</span></span>
<span data-ttu-id="e6b64-103">コントロールが関数に渡されることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e6b64-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6b64-104">`FunctionEnter` .NET framework version 2.0 では、関数は廃止されており、その使用はパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="e6b64-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="e6b64-105">使用して、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e6b64-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b64-106">構文</span><span class="sxs-lookup"><span data-stu-id="e6b64-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6b64-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e6b64-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="e6b64-108">[in]制御が渡されます関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="e6b64-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6b64-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e6b64-109">Remarks</span></span>  
 <span data-ttu-id="e6b64-110">`FunctionEnter`関数コールバックです。 これを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6b64-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="e6b64-111">実装を使用する必要があります、 `__declspec`(`naked`) ストレージ クラス属性。</span><span class="sxs-lookup"><span data-stu-id="e6b64-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="e6b64-112">実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。</span><span class="sxs-lookup"><span data-stu-id="e6b64-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="e6b64-113">エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6b64-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="e6b64-114">終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6b64-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="e6b64-115">実装`FunctionEnter`ガベージ コレクションを遅らせることがあるためにをブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="e6b64-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="e6b64-116">実装は、ガベージ コレクションをしないでスタックはガベージ コレクションに適した状態ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e6b64-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="e6b64-117">ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionEnter`を返します。</span><span class="sxs-lookup"><span data-stu-id="e6b64-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="e6b64-118">また、`FunctionEnter`関数を呼び出してはならないようにまたはマネージ コードにマネージ メモリの割り当て。</span><span class="sxs-lookup"><span data-stu-id="e6b64-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b64-119">要件</span><span class="sxs-lookup"><span data-stu-id="e6b64-119">Requirements</span></span>  
 <span data-ttu-id="e6b64-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e6b64-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b64-121">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="e6b64-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e6b64-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6b64-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6b64-123">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="e6b64-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b64-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6b64-124">See Also</span></span>  
 [<span data-ttu-id="e6b64-125">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="e6b64-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="e6b64-126">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="e6b64-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="e6b64-127">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="e6b64-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="e6b64-128">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="e6b64-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="e6b64-129">プロファイリング グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="e6b64-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
