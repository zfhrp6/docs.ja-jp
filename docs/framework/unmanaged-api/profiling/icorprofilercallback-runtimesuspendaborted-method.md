---
title: ICorProfilerCallback::RuntimeSuspendAborted メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5726c0a563c8937f6f4fff184b7b924d501fa83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451907"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="f5bd9-102">ICorProfilerCallback::RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bd9-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="f5bd9-103">ランタイムが発生しているランタイムの中断を中止されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f5bd9-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5bd9-104">構文</span><span class="sxs-lookup"><span data-stu-id="f5bd9-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5bd9-105">コメント</span><span class="sxs-lookup"><span data-stu-id="f5bd9-105">Remarks</span></span>  
 <span data-ttu-id="f5bd9-106">2 つのスレッドが同時にランタイムの中断を試行した場合は、ランタイムの中断を中断する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f5bd9-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="f5bd9-107">いずれか、 [icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)コールバックまたは`RuntimeSuspendAborted`コールバックは、1 つのスレッド次で発生する[icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="f5bd9-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="f5bd9-108">`RuntimeSuspendAborted`と同じスレッドで発生することが保証コールバック、`RuntimeSuspendStarted`コールバック。</span><span class="sxs-lookup"><span data-stu-id="f5bd9-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5bd9-109">要件</span><span class="sxs-lookup"><span data-stu-id="f5bd9-109">Requirements</span></span>  
 <span data-ttu-id="f5bd9-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5bd9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5bd9-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5bd9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5bd9-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5bd9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5bd9-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5bd9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bd9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5bd9-114">See Also</span></span>  
 [<span data-ttu-id="f5bd9-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5bd9-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
