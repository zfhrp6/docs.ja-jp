---
title: "ICorDebugController::HasQueuedCallbacks メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.HasQueuedCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81830cbadcf9fb359b8e1a74cd47f9d18543c29c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="83045-102">ICorDebugController::HasQueuedCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="83045-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="83045-103">任意のマネージ コールバックが、指定されたスレッドの現在キューに登録するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="83045-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83045-104">構文</span><span class="sxs-lookup"><span data-stu-id="83045-104">Syntax</span></span>  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83045-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83045-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="83045-106">[in]スレッドを表す"ICorDebugThread"オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="83045-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="83045-107">[out]ある値へのポインター`true`任意のマネージ コールバックがいると、指定したスレッドのキューに置かれた、それ以外の場合は`false`します。</span><span class="sxs-lookup"><span data-stu-id="83045-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="83045-108">Null が指定されている場合、`pThread`パラメーター、`HasQueuedCallbacks`戻ります`true`マネージ コールバックが任意のスレッドのキューに存在している場合。</span><span class="sxs-lookup"><span data-stu-id="83045-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83045-109">コメント</span><span class="sxs-lookup"><span data-stu-id="83045-109">Remarks</span></span>  
 <span data-ttu-id="83045-110">コールバックに毎回、一度に 1 つのディスパッチなります[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)と呼びます。</span><span class="sxs-lookup"><span data-stu-id="83045-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="83045-111">デバッガーは、同時に発生する複数のデバッグ イベントを報告する必要がある場合、このフラグを確認できます。</span><span class="sxs-lookup"><span data-stu-id="83045-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="83045-112">デバッグ イベントのキューに入っているときに、既に、発生したため、デバッガーがデバッグ対象の状態を確認するためのキュー全体をドレインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83045-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="83045-113">(呼び出し`ICorDebugController::Continue`するキューのドレインを実行します)。たとえば、キューには、スレッドで 2 つのデバッグ イベントが含まれている場合*X*、デバッガーがスレッドを中断および*X* 、最初のデバッグ イベントとし、呼び出しの後に`ICorDebugController::Continue`、2 番目のデバッグ イベントをスレッド*X*スレッドが中断されましたがディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="83045-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83045-114">要件</span><span class="sxs-lookup"><span data-stu-id="83045-114">Requirements</span></span>  
 <span data-ttu-id="83045-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="83045-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83045-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83045-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83045-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83045-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83045-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83045-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83045-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="83045-119">See Also</span></span>  
 
