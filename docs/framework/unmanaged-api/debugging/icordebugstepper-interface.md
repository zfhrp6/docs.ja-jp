---
title: ICorDebugStepper Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper
helpviewer_keywords: ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 266e8c664ac7c5efa1b199efc522f0b890e38e3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepper-interface1"></a><span data-ttu-id="6d45b-102">ICorDebugStepper Interface1</span><span class="sxs-lookup"><span data-stu-id="6d45b-102">ICorDebugStepper Interface1</span></span>
<span data-ttu-id="6d45b-103">デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="6d45b-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d45b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-104">Methods</span></span>  
  
|<span data-ttu-id="6d45b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-105">Method</span></span>|<span data-ttu-id="6d45b-106">説明</span><span class="sxs-lookup"><span data-stu-id="6d45b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d45b-107">Deactivate メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="6d45b-108">この原因`ICorDebugStepper`を受信した最後のステップ コマンドをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="6d45b-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="6d45b-109">IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="6d45b-110">示す値を取得するかどうかこの`ICorDebugStepper`ステップが現在実行中です。</span><span class="sxs-lookup"><span data-stu-id="6d45b-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="6d45b-111">SetInterceptMask メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="6d45b-112">ステップ インできるコードの型を指定する CorDebugIntercept 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="6d45b-113">SetRangeIL メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="6d45b-114">示す値を設定するかどうかを呼び出す[icordebugstepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)にステップ スルーされるが、メソッドの Microsoft intermediate language (MSIL) コードまたはネイティブ コードへの相対引数の値を渡します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="6d45b-115">SetUnmappedStopMask メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="6d45b-116">マップ解除したコードの実行が停止しメッセージの種類を指定する CorDebugUnmappedStop 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="6d45b-117">Step メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="6d45b-118">この原因`ICorDebugStepper`シングル ステップ実行にその格納スレッドおよび必要に応じて、スレッド内で呼び出される関数をシングル ステップ実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="6d45b-119">StepOut メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="6d45b-120">この原因`ICorDebugStepper`ときに完了してその格納スレッドを 1 ステップを現在のフレームが呼び出し元のフレームにコントロールを返します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="6d45b-121">StepRange メソッド</span><span class="sxs-lookup"><span data-stu-id="6d45b-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="6d45b-122">この原因`ICorDebugStepper`シングル ステップ実行し、その格納スレッド場合に返されるに指定された範囲の最後のタスクを超えるコードに到達します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d45b-123">コメント</span><span class="sxs-lookup"><span data-stu-id="6d45b-123">Remarks</span></span>  
 <span data-ttu-id="6d45b-124">`ICorDebugStepper`インターフェイスは、次の目的で機能します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="6d45b-125">ステップ コマンドが発行して、そのコマンドの完了の間で識別子として機能します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="6d45b-126">実行できるすべてのステップ実行をカプセル化する中央のインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="6d45b-127">処理の途中でステップ実行の操作をキャンセルする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="6d45b-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="6d45b-128">スレッドあたり 1 つ以上のステッパことができます。</span><span class="sxs-lookup"><span data-stu-id="6d45b-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="6d45b-129">たとえば、関数のステップ オーバー中に、ブレークポイントにヒットする可能性があり、ユーザーがその関数内の新しいステップ実行操作を開始することもします。</span><span class="sxs-lookup"><span data-stu-id="6d45b-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="6d45b-130">この状況に対処する方法を決定する、デバッガーの責任です。</span><span class="sxs-lookup"><span data-stu-id="6d45b-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="6d45b-131">デバッガーは、元のステップ実行操作をキャンセルするか 2 つの操作を入れ子にできます。</span><span class="sxs-lookup"><span data-stu-id="6d45b-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="6d45b-132">`ICorDebugStepper`インターフェイスが 2 つの選択肢をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6d45b-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="6d45b-133">ステッパは、共通言語ランタイム (CLR) は、マーシャ リングされたクロス スレッド呼び出しを行う場合、スレッド間で移行可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6d45b-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d45b-134">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6d45b-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d45b-135">必要条件</span><span class="sxs-lookup"><span data-stu-id="6d45b-135">Requirements</span></span>  
 <span data-ttu-id="6d45b-136">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6d45b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d45b-137">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d45b-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d45b-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d45b-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d45b-139">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d45b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d45b-140">参照</span><span class="sxs-lookup"><span data-stu-id="6d45b-140">See Also</span></span>  
 [<span data-ttu-id="6d45b-141">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d45b-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
