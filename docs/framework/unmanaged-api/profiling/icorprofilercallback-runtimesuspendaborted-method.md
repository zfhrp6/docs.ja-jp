---
title: "ICorProfilerCallback::RuntimeSuspendAborted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendAborted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d1c181a471763ea0220c081d64af915ca6be149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="725bf-102">ICorProfilerCallback::RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="725bf-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="725bf-103">ランタイムが発生しているランタイムの中断を中止されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="725bf-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="725bf-104">構文</span><span class="sxs-lookup"><span data-stu-id="725bf-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="725bf-105">コメント</span><span class="sxs-lookup"><span data-stu-id="725bf-105">Remarks</span></span>  
 <span data-ttu-id="725bf-106">2 つのスレッドが同時にランタイムの中断を試行した場合は、ランタイムの中断を中断する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="725bf-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="725bf-107">いずれか、 [icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)コールバックまたは`RuntimeSuspendAborted`コールバックは、1 つのスレッド次で発生する[icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="725bf-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="725bf-108">`RuntimeSuspendAborted`と同じスレッドで発生することが保証コールバック、`RuntimeSuspendStarted`コールバック。</span><span class="sxs-lookup"><span data-stu-id="725bf-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="725bf-109">要件</span><span class="sxs-lookup"><span data-stu-id="725bf-109">Requirements</span></span>  
 <span data-ttu-id="725bf-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="725bf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="725bf-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="725bf-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="725bf-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="725bf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="725bf-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="725bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725bf-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="725bf-114">See Also</span></span>  
 [<span data-ttu-id="725bf-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="725bf-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
