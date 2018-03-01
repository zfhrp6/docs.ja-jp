---
title: "ICorProfilerCallback::RuntimeSuspendAborted メソッド"
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
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d62df6fc90a2601997aeb7ecbe410f1a35d7012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="0e873-102">ICorProfilerCallback::RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="0e873-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="0e873-103">ランタイムが発生しているランタイムの中断を中止されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0e873-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e873-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e873-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0e873-105">コメント</span><span class="sxs-lookup"><span data-stu-id="0e873-105">Remarks</span></span>  
 <span data-ttu-id="0e873-106">2 つのスレッドが同時にランタイムの中断を試行した場合は、ランタイムの中断を中断する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0e873-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="0e873-107">いずれか、 [icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)コールバックまたは`RuntimeSuspendAborted`コールバックは、1 つのスレッド次で発生する[icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="0e873-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="0e873-108">`RuntimeSuspendAborted`と同じスレッドで発生することが保証コールバック、`RuntimeSuspendStarted`コールバック。</span><span class="sxs-lookup"><span data-stu-id="0e873-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e873-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="0e873-109">Requirements</span></span>  
 <span data-ttu-id="0e873-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e873-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e873-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0e873-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0e873-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e873-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e873-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e873-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e873-114">参照</span><span class="sxs-lookup"><span data-stu-id="0e873-114">See Also</span></span>  
 [<span data-ttu-id="0e873-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e873-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
