---
title: ICorDebugEval Interface1
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
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77e97e31a20c392eebae1b373bb1af53f87c23e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval-interface1"></a><span data-ttu-id="5c80c-102">ICorDebugEval Interface1</span><span class="sxs-lookup"><span data-stu-id="5c80c-102">ICorDebugEval Interface1</span></span>
<span data-ttu-id="5c80c-103">デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5c80c-103">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c80c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-104">Methods</span></span>  
  
|<span data-ttu-id="5c80c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-105">Method</span></span>|<span data-ttu-id="5c80c-106">説明</span><span class="sxs-lookup"><span data-stu-id="5c80c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c80c-107">Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-107">Abort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|<span data-ttu-id="5c80c-108">この計算を中止`ICorDebugEval`オブジェクトが現在を実行します。</span><span class="sxs-lookup"><span data-stu-id="5c80c-108">Aborts the computation this `ICorDebugEval` object is currently performing.</span></span>|  
|[<span data-ttu-id="5c80c-109">CallFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-109">CallFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|<span data-ttu-id="5c80c-110">指定した関数への呼び出しを設定します。</span><span class="sxs-lookup"><span data-stu-id="5c80c-110">Sets up a call to the specified function.</span></span> <span data-ttu-id="5c80c-111">(.NET Framework version 2.0 で不使用: を使用して[icordebugeval 2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)代わりにします)。</span><span class="sxs-lookup"><span data-stu-id="5c80c-111">(Obsolete in the .NET Framework version 2.0; use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) instead.)</span></span>|  
|[<span data-ttu-id="5c80c-112">CreateValue メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-112">CreateValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|<span data-ttu-id="5c80c-113">0 または null の初期値を持つ、指定した型の"ICorDebugValue"オブジェクトへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5c80c-113">Gets an interface pointer to an "ICorDebugValue" object of the specified type, with an initial value of zero or null.</span></span> <span data-ttu-id="5c80c-114">(.NET Framework 2.0 で不使用: を使用して[icordebugeval 2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)代わりにします)。</span><span class="sxs-lookup"><span data-stu-id="5c80c-114">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.)</span></span>|  
|[<span data-ttu-id="5c80c-115">GetResult メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-115">GetResult Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|<span data-ttu-id="5c80c-116">インターフェイス ポインターを取得、`ICorDebugValue`評価の結果を格納しています。</span><span class="sxs-lookup"><span data-stu-id="5c80c-116">Gets an interface pointer to an `ICorDebugValue` that contains the results of the evaluation.</span></span>|  
|[<span data-ttu-id="5c80c-117">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-117">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|<span data-ttu-id="5c80c-118">"ICorDebugThread"場所この評価が実行中またはこれから実行するには、インターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5c80c-118">Gets an interface pointer to the "ICorDebugThread" where this evaluation is executing or will execute.</span></span>|  
|[<span data-ttu-id="5c80c-119">IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-119">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|<span data-ttu-id="5c80c-120">示す値を取得するかどうかこの`ICorDebugEval`オブジェクトが現在実行中です。</span><span class="sxs-lookup"><span data-stu-id="5c80c-120">Gets a value that indicates whether this `ICorDebugEval` object is currently executing.</span></span>|  
|[<span data-ttu-id="5c80c-121">NewArray メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-121">NewArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|<span data-ttu-id="5c80c-122">指定した要素の型および次元の新しい配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5c80c-122">Allocates a new array of the specified element type and dimensions.</span></span> <span data-ttu-id="5c80c-123">(.NET Framework 2.0 で不使用: を使用して[icordebugeval 2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)代わりにします)。</span><span class="sxs-lookup"><span data-stu-id="5c80c-123">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.)</span></span>|  
|[<span data-ttu-id="5c80c-124">NewObject メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-124">NewObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|<span data-ttu-id="5c80c-125">オブジェクトの新しいインスタンスを割り当てるし、指定したコンス トラクター メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5c80c-125">Allocates a new object instance and calls the specified constructor method.</span></span> <span data-ttu-id="5c80c-126">(.NET Framework 2.0 で不使用: を使用して[icordebugeval 2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)代わりにします)。</span><span class="sxs-lookup"><span data-stu-id="5c80c-126">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.)</span></span>|  
|[<span data-ttu-id="5c80c-127">NewObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-127">NewObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|<span data-ttu-id="5c80c-128">コンス トラクター メソッドを呼び出さずに、指定した型の新しいオブジェクト インスタンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5c80c-128">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span> <span data-ttu-id="5c80c-129">(.NET Framework 2.0 で不使用: を使用して[icordebugeval 2::newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)代わりにします)。</span><span class="sxs-lookup"><span data-stu-id="5c80c-129">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.)</span></span>|  
|[<span data-ttu-id="5c80c-130">NewString メソッド</span><span class="sxs-lookup"><span data-stu-id="5c80c-130">NewString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|<span data-ttu-id="5c80c-131">指定されたコンテンツを持つ新しい文字列オブジェクトを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5c80c-131">Allocates a new string object with the specified contents.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c80c-132">コメント</span><span class="sxs-lookup"><span data-stu-id="5c80c-132">Remarks</span></span>  
 <span data-ttu-id="5c80c-133">`ICorDebugEval`評価を実行するために使用する特定のスレッドのコンテキストでオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5c80c-133">An `ICorDebugEval` object is created in the context of a specific thread that is used to perform the evaluations.</span></span> <span data-ttu-id="5c80c-134">すべてのオブジェクトと特定の評価で使用される型は、同じアプリケーション ドメイン内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c80c-134">All objects and types used in a given evaluation must reside within the same application domain.</span></span> <span data-ttu-id="5c80c-135">そのアプリケーション ドメインでは、スレッドの現在のアプリケーション ドメインと同じである必要がありますされません。</span><span class="sxs-lookup"><span data-stu-id="5c80c-135">That application domain need not be the same as the current application domain of the thread.</span></span> <span data-ttu-id="5c80c-136">評価は、入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5c80c-136">Evaluations can be nested.</span></span>  
  
 <span data-ttu-id="5c80c-137">デバッガーの呼び出しまでの評価の操作を実行しないで[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)、し、受信、 [icordebugmanagedcallback::evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="5c80c-137">The evaluation's operations do not complete until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md), and then receives an [ICorDebugManagedCallback::EvalComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) callback.</span></span> <span data-ttu-id="5c80c-138">その他のスレッドを実行できるようにすることがなく評価の機能を使用する必要がある場合は、いずれかを使用してスレッドを中断[icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)または[icordebugcontroller::stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)呼び出す前に[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c80c-138">If you need to use the evaluation functionality without allowing other threads to run, suspend the threads by using either [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) or [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md) before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
 <span data-ttu-id="5c80c-139">評価が進行中にユーザー コードが実行されているためクラスの読み込みやブレークポイントなどのデバッグ イベントは発生します。</span><span class="sxs-lookup"><span data-stu-id="5c80c-139">Because user code is running when the evaluation is in progress, any debug events can occur, including class loads and breakpoints.</span></span> <span data-ttu-id="5c80c-140">デバッガーは、コールバックをこれらのイベントは通常どおりに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c80c-140">The debugger will receive callbacks, as normal, for these events.</span></span> <span data-ttu-id="5c80c-141">評価の状態は、通常のプログラムの状態の調査の一部として表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c80c-141">The state of the evaluation will be seen as part of the inspection of the normal program state.</span></span> <span data-ttu-id="5c80c-142">スタック チェーンがされます、`CHAIN_FUNC_EVAL`チェーン ("CorDebugStepReason"列挙型を参照してください、 [icordebugchain::getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)メソッド)。</span><span class="sxs-lookup"><span data-stu-id="5c80c-142">The stack chain will be a `CHAIN_FUNC_EVAL` chain (see the "CorDebugStepReason" enumeration and the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method).</span></span> <span data-ttu-id="5c80c-143">完全なデバッガー API は、通常どおりに動作し続けます。</span><span class="sxs-lookup"><span data-stu-id="5c80c-143">The full debugger API will continue to operate as normal.</span></span>  
  
 <span data-ttu-id="5c80c-144">デッドロック状態または無限ループの状況が発生した場合、ユーザー コードが完了しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5c80c-144">If a deadlocked or infinite looping situation arises, the user code may never complete.</span></span> <span data-ttu-id="5c80c-145">このような場合は、呼び出す必要があります[icordebugeval::abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)プログラムを再開する前にします。</span><span class="sxs-lookup"><span data-stu-id="5c80c-145">In such a case, you must call [ICorDebugEval::Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) before resuming the program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c80c-146">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5c80c-146">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c80c-147">必要条件</span><span class="sxs-lookup"><span data-stu-id="5c80c-147">Requirements</span></span>  
 <span data-ttu-id="5c80c-148">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c80c-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c80c-149">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c80c-149">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c80c-150">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c80c-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c80c-151">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c80c-151">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c80c-152">参照</span><span class="sxs-lookup"><span data-stu-id="5c80c-152">See Also</span></span>  
    
    
    
 [<span data-ttu-id="5c80c-153">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c80c-153">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
