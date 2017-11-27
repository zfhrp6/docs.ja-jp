---
title: "ICorProfilerCallback::RuntimeResumeFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeResumeFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d923db2d9614a4cf7ebc4f1d910a86fee85a0bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="8aea7-102">ICorProfilerCallback::RuntimeResumeFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="8aea7-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="8aea7-103">ランタイムはランタイムのすべてのスレッドが再開し、通常の操作に返されますが、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8aea7-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aea7-104">構文</span><span class="sxs-lookup"><span data-stu-id="8aea7-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8aea7-105">コメント</span><span class="sxs-lookup"><span data-stu-id="8aea7-105">Remarks</span></span>  
 <span data-ttu-id="8aea7-106">`RuntimeResumeFinished`と同じスレッドで発生するコールバックは保証されません、 [icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="8aea7-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="8aea7-107">ただし、必ずと同じスレッドで発生する、 [icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="8aea7-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aea7-108">要件</span><span class="sxs-lookup"><span data-stu-id="8aea7-108">Requirements</span></span>  
 <span data-ttu-id="8aea7-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8aea7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aea7-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8aea7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8aea7-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aea7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aea7-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aea7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aea7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8aea7-113">See Also</span></span>  
 [<span data-ttu-id="8aea7-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8aea7-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
