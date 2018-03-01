---
title: "ICorDebugUnmanagedCallback::DebugEvent メソッド"
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
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49c3386fcda0bc731935ec9db7d029d0e619ef14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="a61aa-102">ICorDebugUnmanagedCallback::DebugEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="a61aa-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="a61aa-103">ネイティブ イベントが発生したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a61aa-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a61aa-104">構文</span><span class="sxs-lookup"><span data-stu-id="a61aa-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a61aa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a61aa-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="a61aa-106">[in]ネイティブ イベントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a61aa-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="a61aa-107">[in]`true`デバッガー呼び出すまで、管理されていないイベントの発生後、管理対象プロセスの状態との対話が可能な場合、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)、それ以外の`false`します。</span><span class="sxs-lookup"><span data-stu-id="a61aa-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a61aa-108">コメント</span><span class="sxs-lookup"><span data-stu-id="a61aa-108">Remarks</span></span>  
 <span data-ttu-id="a61aa-109">デバッグ中のスレッドが Win32 スレッドの場合は、デバッグのインターフェイス、Win32 のメンバーは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a61aa-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="a61aa-110">呼び出すことができます`ICorDebugController::Continue`Win32 スレッドでのみ、および過去の帯域外のイベントを続行するときのみです。</span><span class="sxs-lookup"><span data-stu-id="a61aa-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="a61aa-111">`DebugEvent`コールバックがコールバックの標準的な規則に従っていません。</span><span class="sxs-lookup"><span data-stu-id="a61aa-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="a61aa-112">呼び出すと`DebugEvent`プロセスになります、raw、OS デバッグの停止状態。</span><span class="sxs-lookup"><span data-stu-id="a61aa-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="a61aa-113">プロセスは同期されません。</span><span class="sxs-lookup"><span data-stu-id="a61aa-113">The process will not be synchronized.</span></span> <span data-ttu-id="a61aa-114">それ以外の入れ子になる可能性があります、マネージ コードに関する情報の要求を満たすために必要な場合に同期済みの状態は自動的に入力`DebugEvent`コールバック。</span><span class="sxs-lookup"><span data-stu-id="a61aa-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="a61aa-115">呼び出す[icordebugprocess::clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)プロセスを続行する前に、例外イベントを無視するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="a61aa-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="a61aa-116">このメソッドを呼び出すと、要求では、続行、DBG_EXCEPTION_NOT_HANDLED ではなく DBG_CONTINUE を送信し、帯域外のブレークポイントとシングル ステップ例外を自動的にクリアします。</span><span class="sxs-lookup"><span data-stu-id="a61aa-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="a61aa-117">デバッグ中のアプリケーションが停止した場合でも、および未処理の帯域内のイベントが既に存在する場合、帯域外のイベントは、いつでも取得できます。</span><span class="sxs-lookup"><span data-stu-id="a61aa-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="a61aa-118">.NET framework version 2.0 では、デバッガーを過去の帯域外のブレークポイント イベント続行すぐにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a61aa-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="a61aa-119">デバッガーを使用する必要があります、 [icordebugprocess 2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)と[icordebugprocess 2::clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)メソッドを追加して、ブレークポイントを削除します。</span><span class="sxs-lookup"><span data-stu-id="a61aa-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="a61aa-120">これらのメソッドは、帯域外のブレークポイントを自動的にスキップされます。</span><span class="sxs-lookup"><span data-stu-id="a61aa-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="a61aa-121">したがって、ディスパッチのみの帯域外のブレークポイントは、Win32 への呼び出しなど、命令ストリーム内に既にある生のブレークポイントをする必要があります`DebugBreak`関数。</span><span class="sxs-lookup"><span data-stu-id="a61aa-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="a61aa-122">使用しないでください`ICorDebugProcess::ClearCurrentException`、 [icordebugprocess::getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)、 [icordebugprocess::setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)、または、他のメンバー、[デバッグ API](../../../../docs/framework/unmanaged-api/debugging/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="a61aa-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a61aa-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="a61aa-123">Requirements</span></span>  
 <span data-ttu-id="a61aa-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a61aa-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a61aa-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a61aa-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a61aa-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a61aa-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a61aa-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a61aa-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61aa-128">参照</span><span class="sxs-lookup"><span data-stu-id="a61aa-128">See Also</span></span>  
 [<span data-ttu-id="a61aa-129">ICorDebugUnmanagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a61aa-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
