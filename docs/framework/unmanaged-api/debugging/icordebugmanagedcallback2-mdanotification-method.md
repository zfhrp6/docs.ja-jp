---
title: "ICorDebugManagedCallback2::MDANotification メソッド"
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
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a58e286feb3387557d0a37c463f2af67abf8cc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="55076-102">ICorDebugManagedCallback2::MDANotification メソッド</span><span class="sxs-lookup"><span data-stu-id="55076-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="55076-103">コードが実行されるは、デバッグ中のアプリケーションでマネージ デバッグ アシスタント (MDA) が発生したことの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="55076-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55076-104">構文</span><span class="sxs-lookup"><span data-stu-id="55076-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55076-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55076-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="55076-106">[in]プロセスを公開する ICorDebugController インターフェイスまたは MDA が発生したアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55076-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="55076-107">デバッガーしないようにコント ローラーは、プロセスまたはアプリケーション ドメイン、かどうかについて、推測に基づいて、判断を行うインターフェイスを常に照会できることができます。</span><span class="sxs-lookup"><span data-stu-id="55076-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="55076-108">[in]デバッグ イベントが発生したマネージ スレッドを公開する ICorDebugThread インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55076-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="55076-109">MDA がアンマネージで発生した場合のスレッドの値`pThread`は null になります。</span><span class="sxs-lookup"><span data-stu-id="55076-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="55076-110">オペレーティング システム (OS) のスレッド ID は、MDA オブジェクト自体から取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55076-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="55076-111">[in]ポインター、 [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA の情報を公開するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="55076-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55076-112">コメント</span><span class="sxs-lookup"><span data-stu-id="55076-112">Remarks</span></span>  
 <span data-ttu-id="55076-113">MDA はヒューリスティック警告であり、呼び出し元を除く任意の明示的なデバッガー アクションは不要[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)デバッグ中は、アプリケーションの実行を再開します。</span><span class="sxs-lookup"><span data-stu-id="55076-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="55076-114">Mda が起動され、どのデータが任意の時点で、特定の MDA では、共通言語ランタイム (CLR) を確認できます。</span><span class="sxs-lookup"><span data-stu-id="55076-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="55076-115">そのため、デバッガーは特定の MDA パターンを必要とするすべての機能を構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55076-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="55076-116">Mda は、キューに置かれ、MDA が検出された直後後に発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55076-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="55076-117">これは、ランタイムが検出したときに MDA を発生させるのではなく、MDA を発生させるための安全なポイントに到達するまで待機する必要がある場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55076-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="55076-118">また、ランタイムは、Mda のキューに置かれたコールバック (「添付」イベントの操作に似ています) の 1 つのセット内の数で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55076-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="55076-119">デバッガーへの参照を解放する必要があります、`ICorDebugMDA`インスタンスから返された後すぐに、 `MDANotification` MDA によって消費されるメモリをリサイクルする CLR のためのコールバック。</span><span class="sxs-lookup"><span data-stu-id="55076-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="55076-120">多数の Mda が発生している場合、インスタンスを解放するとパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55076-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55076-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="55076-121">Requirements</span></span>  
 <span data-ttu-id="55076-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="55076-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55076-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55076-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55076-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55076-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55076-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55076-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55076-126">参照</span><span class="sxs-lookup"><span data-stu-id="55076-126">See Also</span></span>  
 [<span data-ttu-id="55076-127">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="55076-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="55076-128">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55076-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="55076-129">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55076-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
