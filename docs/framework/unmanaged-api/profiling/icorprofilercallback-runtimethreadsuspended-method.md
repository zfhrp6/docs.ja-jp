---
title: "ICorProfilerCallback::RuntimeThreadSuspended メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeThreadSuspended
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d2ab0244e898a60db8fe392ccbd8c0ebfd5523
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="ec208-102">ICorProfilerCallback::RuntimeThreadSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="ec208-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="ec208-103">指定したスレッドを中断したかを中断することをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ec208-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec208-104">構文</span><span class="sxs-lookup"><span data-stu-id="ec208-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec208-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec208-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ec208-106">[in]中断されているスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="ec208-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec208-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ec208-107">Remarks</span></span>  
 <span data-ttu-id="ec208-108">`RuntimeThreadSuspended`通知に間でいつでも発生することができます、 [icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)および関連付けられた[icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="ec208-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="ec208-109">間に発生する通知[icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)と`RuntimeResumeStarted`がで実行しているスレッドがアンマネージ コードと、ランタイムに入ったときに中断されました。</span><span class="sxs-lookup"><span data-stu-id="ec208-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="ec208-110">一般に、このコールバックは、スレッドが中断した直後に発生します。</span><span class="sxs-lookup"><span data-stu-id="ec208-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="ec208-111">ただし、(このコールバックを呼び出したスレッド) の実行中のスレッドが中断される 1 つの場合は、このコールバックが発生スレッドが中断する前にします。</span><span class="sxs-lookup"><span data-stu-id="ec208-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec208-112">要件</span><span class="sxs-lookup"><span data-stu-id="ec208-112">Requirements</span></span>  
 <span data-ttu-id="ec208-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ec208-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec208-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec208-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec208-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec208-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec208-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec208-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec208-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec208-117">See Also</span></span>  
 [<span data-ttu-id="ec208-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec208-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ec208-119">RuntimeThreadResumed メソッド</span><span class="sxs-lookup"><span data-stu-id="ec208-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
