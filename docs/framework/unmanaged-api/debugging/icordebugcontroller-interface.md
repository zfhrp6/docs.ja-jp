---
title: ICorDebugController Interface1
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
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bde0ef86ff6304c696ad8c68fc81c0a339ed6e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="866d6-102">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="866d6-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="866d6-103">コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="866d6-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="866d6-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-104">Methods</span></span>  
  
|<span data-ttu-id="866d6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-105">Method</span></span>|<span data-ttu-id="866d6-106">説明</span><span class="sxs-lookup"><span data-stu-id="866d6-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="866d6-107">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="866d6-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="866d6-108">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="866d6-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="866d6-109">Continue メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="866d6-110">呼び出しの後にマネージ スレッドの実行を再開[icordebugcontroller::stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="866d6-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="866d6-111">Detach メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="866d6-112">プロセスまたはアプリケーション ドメインからデバッガーをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="866d6-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="866d6-113">EnumerateThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="866d6-114">プロセスのアクティブなマネージ スレッドの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="866d6-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="866d6-115">HasQueuedCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="866d6-116">任意のマネージ コールバックが、指定されたスレッドの現在キューに登録するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="866d6-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="866d6-117">IsRunning メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="866d6-118">プロセス内のスレッドが自由に実行中かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="866d6-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="866d6-119">SetAllThreadsDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="866d6-120">プロセスのすべてのマネージ スレッドのデバッグ状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="866d6-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="866d6-121">Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="866d6-122">プロセスでマネージ コードを実行しているすべてのスレッドを協調停止を実行します。</span><span class="sxs-lookup"><span data-stu-id="866d6-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="866d6-123">Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="866d6-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="866d6-124">指定した終了コードを使用して、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="866d6-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="866d6-125">コメント</span><span class="sxs-lookup"><span data-stu-id="866d6-125">Remarks</span></span>  
 <span data-ttu-id="866d6-126">場合`ICorDebugController`がプロセスを制御するには、スコープには、プロセスのすべてのスレッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="866d6-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="866d6-127">場合`ICorDebugController`がアプリケーション ドメインを制御するには、スコープにはその特定のアプリケーション ドメインのスレッドのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="866d6-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="866d6-128">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="866d6-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="866d6-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="866d6-129">Requirements</span></span>  
 <span data-ttu-id="866d6-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="866d6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="866d6-131">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="866d6-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="866d6-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="866d6-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="866d6-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="866d6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="866d6-134">参照</span><span class="sxs-lookup"><span data-stu-id="866d6-134">See Also</span></span>  
 [<span data-ttu-id="866d6-135">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="866d6-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
