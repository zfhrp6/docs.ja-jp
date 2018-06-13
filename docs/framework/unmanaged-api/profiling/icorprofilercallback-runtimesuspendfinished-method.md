---
title: ICorProfilerCallback::RuntimeSuspendFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b243c507171a4d907ef4594ae0c715a074c965a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452219"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="dd32d-102">ICorProfilerCallback::RuntimeSuspendFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="dd32d-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="dd32d-103">ランタイムがランタイムのすべてのスレッドの中断を完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="dd32d-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd32d-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd32d-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="dd32d-105">コメント</span><span class="sxs-lookup"><span data-stu-id="dd32d-105">Remarks</span></span>  
 <span data-ttu-id="dd32d-106">アンマネージ コード内にあるすべてのランタイムのスレッドは、ランタイムを再入力するまで実行を続行が許可されます。</span><span class="sxs-lookup"><span data-stu-id="dd32d-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="dd32d-107">その時点で、中断されます、ランタイムが再開されるまでです。</span><span class="sxs-lookup"><span data-stu-id="dd32d-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="dd32d-108">これは、新しいスレッドがランタイムに入ることにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="dd32d-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="dd32d-109">ランタイムのすべてのスレッドは、いずれかの即座に中断され、割り込み可能なコードではすでにまたは割り込み可能なコードに到達したときに中断するように求められます。</span><span class="sxs-lookup"><span data-stu-id="dd32d-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="dd32d-110">`RuntimeSuspendFinished`と同じスレッドで発生することが保証コールバック、 [icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="dd32d-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd32d-111">要件</span><span class="sxs-lookup"><span data-stu-id="dd32d-111">Requirements</span></span>  
 <span data-ttu-id="dd32d-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd32d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd32d-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd32d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd32d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd32d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd32d-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd32d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd32d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd32d-116">See Also</span></span>  
 [<span data-ttu-id="dd32d-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd32d-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dd32d-118">RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="dd32d-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
