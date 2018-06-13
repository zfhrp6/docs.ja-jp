---
title: ICorProfilerCallback::RuntimeThreadSuspended メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7673d6fac2626bc0059204ea77a23686b11638cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452736"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="0dce5-102">ICorProfilerCallback::RuntimeThreadSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="0dce5-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="0dce5-103">指定したスレッドを中断したかを中断することをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0dce5-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dce5-104">構文</span><span class="sxs-lookup"><span data-stu-id="0dce5-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0dce5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0dce5-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="0dce5-106">[in]中断されているスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="0dce5-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dce5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="0dce5-107">Remarks</span></span>  
 <span data-ttu-id="0dce5-108">`RuntimeThreadSuspended`通知に間でいつでも発生することができます、 [icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)および関連付けられた[icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="0dce5-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="0dce5-109">間に発生する通知[icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)と`RuntimeResumeStarted`がで実行しているスレッドがアンマネージ コードと、ランタイムに入ったときに中断されました。</span><span class="sxs-lookup"><span data-stu-id="0dce5-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="0dce5-110">一般に、このコールバックは、スレッドが中断した直後に発生します。</span><span class="sxs-lookup"><span data-stu-id="0dce5-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="0dce5-111">ただし、(このコールバックを呼び出したスレッド) の実行中のスレッドが中断される 1 つの場合は、このコールバックが発生スレッドが中断する前にします。</span><span class="sxs-lookup"><span data-stu-id="0dce5-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dce5-112">要件</span><span class="sxs-lookup"><span data-stu-id="0dce5-112">Requirements</span></span>  
 <span data-ttu-id="0dce5-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0dce5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dce5-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0dce5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0dce5-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dce5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dce5-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dce5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dce5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dce5-117">See Also</span></span>  
 [<span data-ttu-id="0dce5-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0dce5-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="0dce5-119">RuntimeThreadResumed メソッド</span><span class="sxs-lookup"><span data-stu-id="0dce5-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
