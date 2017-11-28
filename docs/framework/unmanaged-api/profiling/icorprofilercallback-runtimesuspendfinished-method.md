---
title: "ICorProfilerCallback::RuntimeSuspendFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c922ee4f986df22f213820b8aed60ea28a76377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="cb9ab-102">ICorProfilerCallback::RuntimeSuspendFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="cb9ab-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="cb9ab-103">ランタイムがランタイムのすべてのスレッドの中断を完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cb9ab-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb9ab-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb9ab-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cb9ab-105">コメント</span><span class="sxs-lookup"><span data-stu-id="cb9ab-105">Remarks</span></span>  
 <span data-ttu-id="cb9ab-106">アンマネージ コード内にあるすべてのランタイムのスレッドは、ランタイムを再入力するまで実行を続行が許可されます。</span><span class="sxs-lookup"><span data-stu-id="cb9ab-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="cb9ab-107">その時点で、中断されます、ランタイムが再開されるまでです。</span><span class="sxs-lookup"><span data-stu-id="cb9ab-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="cb9ab-108">これは、新しいスレッドがランタイムに入ることにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="cb9ab-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="cb9ab-109">ランタイムのすべてのスレッドは、いずれかの即座に中断され、割り込み可能なコードではすでにまたは割り込み可能なコードに到達したときに中断するように求められます。</span><span class="sxs-lookup"><span data-stu-id="cb9ab-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="cb9ab-110">`RuntimeSuspendFinished`と同じスレッドで発生することが保証コールバック、 [icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="cb9ab-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb9ab-111">要件</span><span class="sxs-lookup"><span data-stu-id="cb9ab-111">Requirements</span></span>  
 <span data-ttu-id="cb9ab-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb9ab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb9ab-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb9ab-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb9ab-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb9ab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb9ab-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb9ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9ab-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb9ab-116">See Also</span></span>  
 [<span data-ttu-id="cb9ab-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb9ab-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="cb9ab-118">RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="cb9ab-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
