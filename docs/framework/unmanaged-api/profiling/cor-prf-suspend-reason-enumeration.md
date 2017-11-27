---
title: "COR_PRF_SUSPEND_REASON 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SUSPEND_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SUSPEND_REASON
helpviewer_keywords: COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aef9688d3da047645d53f6fcf113153393780c8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="2a1e9-102">COR_PRF_SUSPEND_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a1e9-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="2a1e9-103">ランタイムが中断された理由を示します。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1e9-104">構文</span><span class="sxs-lookup"><span data-stu-id="2a1e9-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="2a1e9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2a1e9-105">Members</span></span>  
  
|<span data-ttu-id="2a1e9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2a1e9-106">Member</span></span>|<span data-ttu-id="2a1e9-107">説明</span><span class="sxs-lookup"><span data-stu-id="2a1e9-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="2a1e9-108">ランタイムは、不明な理由の中断されています。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="2a1e9-109">ランタイムは、ガベージ コレクションの要求の処理を中断します。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="2a1e9-110">ガベージ コレクションに関連するコールバックの間で発生する、 [icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)と[icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="2a1e9-111">ランタイムが中断されているように、`AppDomain`シャット ダウンできます。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="2a1e9-112">ランタイムが中断されている間、ランタイムはスレッドを判別に、`AppDomain`はシャット ダウンされ、中断するときに設定しています。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="2a1e9-113">ない`AppDomain`-この保留中の特定のコールバック。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="2a1e9-114">コード ピッチを実行できるように、ランタイムが中断されます。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="2a1e9-115">コード ピッチ ・ イン タイム (JIT) コンパイラがのときだけアクティブなコード ピッチが有効になっているが発生します。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="2a1e9-116">ピッチング コールバックの間で発生するコード、`ICorProfilerCallback::RuntimeSuspendFinished`と`ICorProfilerCallback::RuntimeResumeStarted`コールバック。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="2a1e9-117">**注:** 2.0 でこの値は使用されませんので、CLR JIT が .NET framework version 2.0 では、関数をピッチされません。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="2a1e9-118">ランタイムは中断、終了できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="2a1e9-119">操作を完了するすべてのスレッドを中断にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="2a1e9-120">ランタイムは、プロセスのデバッグの中断されています。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="2a1e9-121">ランタイムがガベージ コレクションの準備に中断されます。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="2a1e9-122">ランタイムは、JIT 再コンパイルの中断されています。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a1e9-123">コメント</span><span class="sxs-lookup"><span data-stu-id="2a1e9-123">Remarks</span></span>  
 <span data-ttu-id="2a1e9-124">アンマネージ コード内にあるすべてのランタイムのスレッドは、この時点で、中断されます、ランタイムが再開されるまで、ランタイムを再入力するまで実行を続行が許可されます。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="2a1e9-125">これは、新しいスレッドがランタイムに入ることにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="2a1e9-126">ランタイム内のすべてのスレッドが可能なコード内にある場合、すぐに中断されているか、中断可能なコードに到達したときに中断します。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a1e9-127">要件</span><span class="sxs-lookup"><span data-stu-id="2a1e9-127">Requirements</span></span>  
 <span data-ttu-id="2a1e9-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a1e9-129">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a1e9-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a1e9-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a1e9-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a1e9-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a1e9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a1e9-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a1e9-132">See Also</span></span>  
 [<span data-ttu-id="2a1e9-133">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="2a1e9-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
