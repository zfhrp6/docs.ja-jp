---
title: COR_PRF_SUSPEND_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f4382c7fa85008de9e67ad21c467402bae4ac90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451283"
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="00f13-102">COR_PRF_SUSPEND_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="00f13-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="00f13-103">ランタイムが中断された理由を示します。</span><span class="sxs-lookup"><span data-stu-id="00f13-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f13-104">構文</span><span class="sxs-lookup"><span data-stu-id="00f13-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="00f13-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="00f13-105">Members</span></span>  
  
|<span data-ttu-id="00f13-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="00f13-106">Member</span></span>|<span data-ttu-id="00f13-107">説明</span><span class="sxs-lookup"><span data-stu-id="00f13-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="00f13-108">ランタイムは、不明な理由の中断されています。</span><span class="sxs-lookup"><span data-stu-id="00f13-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="00f13-109">ランタイムは、ガベージ コレクションの要求の処理を中断します。</span><span class="sxs-lookup"><span data-stu-id="00f13-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="00f13-110">ガベージ コレクションに関連するコールバックの間で発生する、 [icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)と[icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="00f13-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="00f13-111">ランタイムが中断されているように、`AppDomain`シャット ダウンできます。</span><span class="sxs-lookup"><span data-stu-id="00f13-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="00f13-112">ランタイムが中断されている間、ランタイムはスレッドを判別に、`AppDomain`はシャット ダウンされ、中断するときに設定しています。</span><span class="sxs-lookup"><span data-stu-id="00f13-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="00f13-113">ない`AppDomain`-この保留中の特定のコールバック。</span><span class="sxs-lookup"><span data-stu-id="00f13-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="00f13-114">コード ピッチを実行できるように、ランタイムが中断されます。</span><span class="sxs-lookup"><span data-stu-id="00f13-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="00f13-115">コード ピッチ ・ イン タイム (JIT) コンパイラがのときだけアクティブなコード ピッチが有効になっているが発生します。</span><span class="sxs-lookup"><span data-stu-id="00f13-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="00f13-116">ピッチング コールバックの間で発生するコード、`ICorProfilerCallback::RuntimeSuspendFinished`と`ICorProfilerCallback::RuntimeResumeStarted`コールバック。</span><span class="sxs-lookup"><span data-stu-id="00f13-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="00f13-117">**注:** 2.0 でこの値は使用されませんので、CLR JIT が .NET framework version 2.0 では、関数をピッチされません。</span><span class="sxs-lookup"><span data-stu-id="00f13-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="00f13-118">ランタイムは中断、終了できるようにします。</span><span class="sxs-lookup"><span data-stu-id="00f13-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="00f13-119">操作を完了するすべてのスレッドを中断にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00f13-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="00f13-120">ランタイムは、プロセスのデバッグの中断されています。</span><span class="sxs-lookup"><span data-stu-id="00f13-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="00f13-121">ランタイムがガベージ コレクションの準備に中断されます。</span><span class="sxs-lookup"><span data-stu-id="00f13-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="00f13-122">ランタイムは、JIT 再コンパイルの中断されています。</span><span class="sxs-lookup"><span data-stu-id="00f13-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00f13-123">コメント</span><span class="sxs-lookup"><span data-stu-id="00f13-123">Remarks</span></span>  
 <span data-ttu-id="00f13-124">アンマネージ コード内にあるすべてのランタイムのスレッドは、この時点で、中断されます、ランタイムが再開されるまで、ランタイムを再入力するまで実行を続行が許可されます。</span><span class="sxs-lookup"><span data-stu-id="00f13-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="00f13-125">これは、新しいスレッドがランタイムに入ることにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="00f13-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="00f13-126">ランタイム内のすべてのスレッドが可能なコード内にある場合、すぐに中断されているか、中断可能なコードに到達したときに中断します。</span><span class="sxs-lookup"><span data-stu-id="00f13-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f13-127">要件</span><span class="sxs-lookup"><span data-stu-id="00f13-127">Requirements</span></span>  
 <span data-ttu-id="00f13-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="00f13-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f13-129">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00f13-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00f13-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00f13-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00f13-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f13-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f13-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="00f13-132">See Also</span></span>  
 [<span data-ttu-id="00f13-133">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="00f13-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
