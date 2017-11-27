---
title: "ICorProfilerInfo3::RequestProfilerDetach メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.RequestProfilerDetach Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d155c68f1b7743e0a888c78f6eeecf967c16570
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a><span data-ttu-id="a0b69-102">ICorProfilerInfo3::RequestProfilerDetach メソッド</span><span class="sxs-lookup"><span data-stu-id="a0b69-102">ICorProfilerInfo3::RequestProfilerDetach Method</span></span>
<span data-ttu-id="a0b69-103">プロファイラーをデタッチするようにランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="a0b69-103">Instructs the runtime to detach the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b69-104">構文</span><span class="sxs-lookup"><span data-stu-id="a0b69-104">Syntax</span></span>  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0b69-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0b69-105">Parameters</span></span>  
 `dwExpectedCompletionMilliseconds`  
 <span data-ttu-id="a0b69-106">[in] プロファイラーをアンロードするのが安全かどうかを確認するチェックを行うまでに共通言語ランタイム (CLR) が待機する時間 (ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="a0b69-106">[in] The length of time, in milliseconds, the common language runtime (CLR) should wait before checking to see whether it is safe to unload the profiler.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0b69-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0b69-107">Return Value</span></span>  
 <span data-ttu-id="a0b69-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="a0b69-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a0b69-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0b69-109">HRESULT</span></span>|<span data-ttu-id="a0b69-110">説明</span><span class="sxs-lookup"><span data-stu-id="a0b69-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0b69-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0b69-111">S_OK</span></span>|<span data-ttu-id="a0b69-112">デタッチ要求は有効です。またデタッチ プロシージャは別のスレッドで継続しています。</span><span class="sxs-lookup"><span data-stu-id="a0b69-112">The detach request is valid, and the detach procedure is now continuing on another thread.</span></span> <span data-ttu-id="a0b69-113">デタッチが完了すると、`ProfilerDetachSucceeded` イベントが発行されます。</span><span class="sxs-lookup"><span data-stu-id="a0b69-113">When the detach is fully complete, a `ProfilerDetachSucceeded` event is issued.</span></span>|  
|<span data-ttu-id="a0b69-114">E_ CORPROF_E_CALLBACK3_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="a0b69-114">E_ CORPROF_E_CALLBACK3_REQUIRED</span></span>|<span data-ttu-id="a0b69-115">プロファイラーが失敗しました、 [iunknown::queryinterface](http://go.microsoft.com/fwlink/?LinkID=144867)の試行、 [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)インターフェイスで、デタッチ操作をサポートするために実装する必要がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0b69-115">The profiler failed an [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) attempt for the [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interface, which it must implement to support the detach operation.</span></span> <span data-ttu-id="a0b69-116">デタッチは試行されませんでした。</span><span class="sxs-lookup"><span data-stu-id="a0b69-116">Detach was not attempted.</span></span>|  
|<span data-ttu-id="a0b69-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span><span class="sxs-lookup"><span data-stu-id="a0b69-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span></span>|<span data-ttu-id="a0b69-118">プロファイラーが起動時に変更できないフラグを設定しているため、デタッチできません。</span><span class="sxs-lookup"><span data-stu-id="a0b69-118">Detachment is impossible because the profiler set immutable flags at startup.</span></span> <span data-ttu-id="a0b69-119">デタッチは試行されませんでした。プロファイラーは完全にアタッチされたままです。</span><span class="sxs-lookup"><span data-stu-id="a0b69-119">Detachment was not attempted; the profiler is still fully attached.</span></span>|  
|<span data-ttu-id="a0b69-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span><span class="sxs-lookup"><span data-stu-id="a0b69-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span></span>|<span data-ttu-id="a0b69-121">デタッチは、プロファイラーを使用するには、Microsoft intermediate language (MSIL) コードがインストルメント化されているため不可能または挿入された`enter` / `leave`フックします。</span><span class="sxs-lookup"><span data-stu-id="a0b69-121">Detachment is impossible because the profiler used instrumented Microsoft intermediate language (MSIL) code, or inserted `enter`/`leave` hooks.</span></span> <span data-ttu-id="a0b69-122">デタッチは試行されませんでした。プロファイラーは完全にアタッチされたままです。</span><span class="sxs-lookup"><span data-stu-id="a0b69-122">Detachment was not attempted; the profiler is still fully attached.</span></span><br /><br /> <span data-ttu-id="a0b69-123">**注**インストルメント化した MSIL は、コードを使用してプロファイラーによって提供されるコードでは、 [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a0b69-123">**Note** Instrumented MSIL is code is code that is provided by the profiler using the [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>|  
|<span data-ttu-id="a0b69-124">CORPROF_E_RUNTIME_UNINITIALIZED</span><span class="sxs-lookup"><span data-stu-id="a0b69-124">CORPROF_E_RUNTIME_UNINITIALIZED</span></span>|<span data-ttu-id="a0b69-125">マネージ アプリケーションでランタイムがまだ初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="a0b69-125">The runtime has not been initialized yet in the managed application.</span></span> <span data-ttu-id="a0b69-126">(つまり、ランタイムは完全には読み込まれていません。)プロファイラーのコールバックの内部にデタッチが要求される場合、このエラー コードが返される可能性があります[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a0b69-126">(That is, the runtime has not been fully loaded.) This error code may be returned when detachment is requested inside the profiler callback's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) method.</span></span>|  
|<span data-ttu-id="a0b69-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0b69-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span></span>|<span data-ttu-id="a0b69-128">サポートされていないタイミングで `RequestProfilerDetach` が呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="a0b69-128">`RequestProfilerDetach` was called at an unsupported time.</span></span> <span data-ttu-id="a0b69-129">これは、いない内からでは、マネージ スレッドでメソッドを呼び出した場合に発生、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)メソッド、または内から、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)ガベージ コレクションを許容できないメソッドです。</span><span class="sxs-lookup"><span data-stu-id="a0b69-129">This occurs if the method is called on a managed thread but not from within an [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) method or from within an [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) method that cannot tolerate a garbage collection.</span></span> <span data-ttu-id="a0b69-130">詳細については、次を参照してください。 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0b69-130">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0b69-131">コメント</span><span class="sxs-lookup"><span data-stu-id="a0b69-131">Remarks</span></span>  
 <span data-ttu-id="a0b69-132">デタッチ プロシージャの実行中に、デタッチ スレッド (プロファイラーのデタッチのために作成されたスレッド) は、すべてのスレッドがプロファイラーのコードを終了したかどうかを時々チェックします。</span><span class="sxs-lookup"><span data-stu-id="a0b69-132">During the detach procedure, the detach thread (the thread created specifically for detaching the profiler) occasionally checks whether all threads have exited the profiler’s code.</span></span> <span data-ttu-id="a0b69-133">プロファイラーは、退避が終了するまでの予想時間を、`dwExpectedCompletionMilliseconds` パラメーターを介して提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0b69-133">The profiler should provide an estimate of how long this should take through the `dwExpectedCompletionMilliseconds` parameter.</span></span> <span data-ttu-id="a0b69-134">使用に適した値は、特定の `ICorProfilerCallback*` メソッド内でプロファイラーが使う通常の時間です。この値は、プロファイラーが使うと想定される最大時間の半分未満にしないでください。</span><span class="sxs-lookup"><span data-stu-id="a0b69-134">A good value to use is the typical amount of time the profiler spends inside any given `ICorProfilerCallback*` method; this value should not be less than half of the maximum amount of time the profiler expects to spend.</span></span>  
  
 <span data-ttu-id="a0b69-135">デタッチ スレッドでは `dwExpectedCompletionMilliseconds` を使用して、プロファイラーのコールバック コードがすべてのスタックからポップされたかどうかをチェックする前にスリープする時間の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0b69-135">The detach thread uses `dwExpectedCompletionMilliseconds` to decide how long to sleep before checking whether profiler callback code has been popped off all stacks.</span></span> <span data-ttu-id="a0b69-136">次のアルゴリズムの詳細は今後の CLR のリリースで変更される可能性がありますが、これはプロファイラーをアンロードしても安全なタイミングを決定するために `dwExpectedCompletionMilliseconds` を利用する 1 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a0b69-136">Although the details of the following algorithm may change in future releases of the CLR, it illustrates one way `dwExpectedCompletionMilliseconds` can be used when determining when it is safe to unload the profiler.</span></span> <span data-ttu-id="a0b69-137">デタッチ スレッドはまず `dwExpectedCompletionMilliseconds` ミリ秒間、スリープ状態になります。</span><span class="sxs-lookup"><span data-stu-id="a0b69-137">The detach thread first sleeps for `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="a0b69-138">スリープから復帰、後に、CLR はプロファイラーのコールバック コードがまだ存在していることを検出した場合は、デタッチ スレッドがスリープ状態再び、今度は 2 回用`dwExpectedCompletionMilliseconds`(ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="a0b69-138">If, after awakening from the sleep, the CLR finds that profiler callback code is still present, the detach thread sleeps again, this time for two times `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="a0b69-139">この 2 回目のスリープから復帰した後に、プロファイラーのコールバック コードがまだ存在することがデタッチ スレッドで検出された場合、再チェックが行われる前に 10 分間、スリープ状態になります。</span><span class="sxs-lookup"><span data-stu-id="a0b69-139">If, after awakening from this second sleep, the detach thread finds that profiler callback code is still present, it sleeps for 10 minutes before checking again.</span></span> <span data-ttu-id="a0b69-140">デタッチ スレッドは継続して 10 分ごとに再チェックを行います。</span><span class="sxs-lookup"><span data-stu-id="a0b69-140">The detach thread continues to recheck every 10 minutes.</span></span>  
  
 <span data-ttu-id="a0b69-141">プロファイラーが `dwExpectedCompletionMilliseconds` を 0 (ゼロ) に指定している場合、CLR は既定値 5000 を使用します。この設定では、チェックが 5 秒後に行われ、その次は 10 秒後に、それ以降は 10 分ごとに再チェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="a0b69-141">If the profiler specifies `dwExpectedCompletionMilliseconds` as 0 (zero), the CLR uses a default value of 5000, which means that it will perform a check after 5 seconds, again after 10 seconds, and then every 10 minutes thereafter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0b69-142">要件</span><span class="sxs-lookup"><span data-stu-id="a0b69-142">Requirements</span></span>  
 <span data-ttu-id="a0b69-143">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0b69-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0b69-144">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0b69-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0b69-145">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0b69-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0b69-146">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0b69-146">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b69-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0b69-147">See Also</span></span>  
 [<span data-ttu-id="a0b69-148">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0b69-148">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="a0b69-149">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0b69-149">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="a0b69-150">プロファイル</span><span class="sxs-lookup"><span data-stu-id="a0b69-150">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
