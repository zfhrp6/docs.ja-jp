---
title: ICorDebugThread Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 404f1bdf5865733648084e34a558b7b20a59b3ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthread-interface1"></a><span data-ttu-id="eea68-102">ICorDebugThread Interface1</span><span class="sxs-lookup"><span data-stu-id="eea68-102">ICorDebugThread Interface1</span></span>
<span data-ttu-id="eea68-103">プロセス内のスレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="eea68-103">Represents a thread in a process.</span></span> <span data-ttu-id="eea68-104">`ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。</span><span class="sxs-lookup"><span data-stu-id="eea68-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eea68-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-105">Methods</span></span>  
  
|<span data-ttu-id="eea68-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-106">Method</span></span>|<span data-ttu-id="eea68-107">説明</span><span class="sxs-lookup"><span data-stu-id="eea68-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eea68-108">ClearCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="eea68-109">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="eea68-109">This method is not implemented.</span></span> <span data-ttu-id="eea68-110">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="eea68-110">Do not use it.</span></span>|  
|[<span data-ttu-id="eea68-111">CreateEval メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="eea68-112">これに動作する ICorDebugEval オブジェクトを作成`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-113">CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="eea68-114">これで、アクティブなフレームをステップ実行を許可する ICorDebugStepper オブジェクトを作成`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-115">EnumerateChains メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="eea68-116">これですべてのスタック チェーンを含む ICorDebugChainEnum 列挙子へのインターフェイス ポインターを取得`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-117">GetActiveChain メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="eea68-118">この active ICorDebugChain へのインターフェイス ポインターを取得`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-119">GetActiveFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="eea68-120">この active ICorDebugFrame へのインターフェイス ポインターを取得`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-121">GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="eea68-122">このアプリケーション ドメインにインターフェイス ポインターを取得`ICorDebugThread`が現在実行中です。</span><span class="sxs-lookup"><span data-stu-id="eea68-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="eea68-123">GetCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="eea68-124">現在、マネージ コードによってスローされる例外を表す ICorDebugValue オブジェクトへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="eea68-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="eea68-125">GetDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="eea68-126">この現在のデバッグ状態を説明する CorDebugThreadState 値を取得`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-127">GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="eea68-128">これのアクティブな部分の現在のハンドルを取得`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-129">GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="eea68-130">これのアクティブな部分の現在のオペレーティング システム識別子を取得`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-131">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="eea68-132">共通言語ランタイム (CLR) のスレッドにインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="eea68-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="eea68-133">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="eea68-134">このプロセスへのインターフェイス ポインターを取得`ICorDebugThread`一部を形成します。</span><span class="sxs-lookup"><span data-stu-id="eea68-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="eea68-135">GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="eea68-136">これに関連付けられたレジスタ セットへのインターフェイス ポインターを取得`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-137">GetUserState メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="eea68-138">この現在の状態を記述する CorDebugUserState 値のビットごとの組み合わせを取得`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="eea68-139">SetDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="eea68-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="eea68-140">ビットごとの組み合わせを設定`CorDebugThreadState`のデバッグ状態を記述する値`ICorDebugThread`です。</span><span class="sxs-lookup"><span data-stu-id="eea68-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eea68-141">コメント</span><span class="sxs-lookup"><span data-stu-id="eea68-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eea68-142">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="eea68-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eea68-143">要件</span><span class="sxs-lookup"><span data-stu-id="eea68-143">Requirements</span></span>  
 <span data-ttu-id="eea68-144">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eea68-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eea68-145">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eea68-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eea68-146">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eea68-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eea68-147">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eea68-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea68-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="eea68-148">See Also</span></span>  
 [<span data-ttu-id="eea68-149">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eea68-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
