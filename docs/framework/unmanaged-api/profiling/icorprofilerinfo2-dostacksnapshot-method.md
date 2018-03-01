---
title: "ICorProfilerInfo2::DoStackSnapshot メソッド"
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
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5548254eb160547643a874fd2e31a085ec6f3ecb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="08daf-102">ICorProfilerInfo2::DoStackSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="08daf-102">ICorProfilerInfo2::DoStackSnapshot Method</span></span>
<span data-ttu-id="08daf-103">指定のスレッドのスタックでマネージ フレームを走査し、コールバックを通じてプロファイラーに情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="08daf-103">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08daf-104">構文</span><span class="sxs-lookup"><span data-stu-id="08daf-104">Syntax</span></span>  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08daf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="08daf-105">Parameters</span></span>  
 `thread`  
 <span data-ttu-id="08daf-106">[in]対象のスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="08daf-106">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="08daf-107">Null を渡す`thread`現在のスレッドのスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="08daf-107">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="08daf-108">場合、`ThreadID`の別のスレッドが渡される、共通言語ランタイム (CLR) そのスレッドを中断、スナップショットを行い、再開します。</span><span class="sxs-lookup"><span data-stu-id="08daf-108">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="08daf-109">[in]実装へのポインター、 [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)各マネージ フレームおよびアンマネージ フレームのそれぞれの実行に関する情報を含む、プロファイラーを提供する CLR によって呼び出されるメソッド。</span><span class="sxs-lookup"><span data-stu-id="08daf-109">[in] A pointer to the implementation of the [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="08daf-110">`StackSnapshotCallback`メソッドは、プロファイラー ライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="08daf-110">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="08daf-111">[in]値、 [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)によって各フレームを渡されるデータの量を指定する列挙体`StackSnapshotCallback`です。</span><span class="sxs-lookup"><span data-stu-id="08daf-111">[in] A value of the [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="08daf-112">[in]渡されるまっすぐクライアントのデータへのポインター、`StackSnapshotCallback`コールバック関数。</span><span class="sxs-lookup"><span data-stu-id="08daf-112">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="08daf-113">[in]Win32 へのポインター`CONTEXT`構造は、これは、スタック ウォークのシードに使用します。</span><span class="sxs-lookup"><span data-stu-id="08daf-113">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="08daf-114">Win32`CONTEXT`構造は、CPU レジスタの値が含まれています、特定の時点での CPU の状態を表します。</span><span class="sxs-lookup"><span data-stu-id="08daf-114">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="08daf-115">シードにより、CLR をアンマネージ ヘルパー コード; 場合は、スタックの一番上に、スタック ウォークを開始する場所を特定します。それ以外の場合、シードは無視されます。</span><span class="sxs-lookup"><span data-stu-id="08daf-115">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="08daf-116">非同期ウォークのシードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08daf-116">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="08daf-117">同期のウォークを実行してシードの必要はありません。</span><span class="sxs-lookup"><span data-stu-id="08daf-117">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="08daf-118">`context`パラメーターが COR_PRF_SNAPSHOT_CONTEXT フラグが渡された場合にのみ有効では、`infoFlags`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="08daf-118">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="08daf-119">[in]サイズ、`CONTEXT`によって参照されている構造体、`context`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="08daf-119">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08daf-120">コメント</span><span class="sxs-lookup"><span data-stu-id="08daf-120">Remarks</span></span>  
 <span data-ttu-id="08daf-121">Null を渡す`thread`現在のスレッドのスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="08daf-121">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="08daf-122">時に対象のスレッドが中断されている場合にのみ、他のスレッドのスナップショットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="08daf-122">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="08daf-123">プロファイラーは、スタック ウォークは、呼び出し`DoStackSnapshot`です。</span><span class="sxs-lookup"><span data-stu-id="08daf-123">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="08daf-124">CLR は、その呼び出しから戻る前に呼び出し、`StackSnapshotCallback`何回か 1 回ごとに管理されているフレーム (またはアンマネージ フレームの実行) スタックにします。</span><span class="sxs-lookup"><span data-stu-id="08daf-124">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="08daf-125">アンマネージ フレームが発生するとを自分でに説明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08daf-125">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="08daf-126">スタックを走査する順序は、フレームがスタックにプッシュされたどの逆: 最後 (最後にプッシュされた) 最初に、メイン (最初プッシュ) フレームをリーフです。</span><span class="sxs-lookup"><span data-stu-id="08daf-126">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="08daf-127">プロファイラーでマネージ スタックをプログラミングする方法の詳細については、次を参照してください。 [、.NET Framework 2.0 におけるプロファイラー スタック ウォーク: 基本と発展](http://go.microsoft.com/fwlink/?LinkId=73638)です。</span><span class="sxs-lookup"><span data-stu-id="08daf-127">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](http://go.microsoft.com/fwlink/?LinkId=73638).</span></span>  
  
 <span data-ttu-id="08daf-128">スタック ウォークは、次のセクションで説明するよう同期または非同期を指定できます。</span><span class="sxs-lookup"><span data-stu-id="08daf-128">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="08daf-129">同期のスタック ウォーク</span><span class="sxs-lookup"><span data-stu-id="08daf-129">Synchronous Stack Walk</span></span>  
 <span data-ttu-id="08daf-130">同期スタック ウォークには、現在のスレッドのスタックのウォーク コールバックへの応答が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08daf-130">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="08daf-131">シードまたは中断は不要です。</span><span class="sxs-lookup"><span data-stu-id="08daf-131">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="08daf-132">同期を行うメソッドを呼び出すのプロファイラーのいずれかを呼び出して、CLR への応答[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (または[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md))、メソッドを呼び出す`DoStackSnapshot`のスタック ウォークを現在のスレッド。</span><span class="sxs-lookup"><span data-stu-id="08daf-132">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (or [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="08daf-133">これは、スタックがどのように通知でなどを表示する場合に役立ちます[icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="08daf-133">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="08daf-134">呼び出すだけで`DoStackSnapshot`内から、`ICorProfilerCallback`で null を渡して、メソッド、`context`と`thread`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="08daf-134">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="08daf-135">非同期のスタック ウォーク</span><span class="sxs-lookup"><span data-stu-id="08daf-135">Asynchronous Stack Walk</span></span>  
 <span data-ttu-id="08daf-136">非同期のスタック ウォークは、別のスレッドのスタックや、コールバックは現在のスレッドの命令ポインターをハイジャックしている応答ではなく、現在のスレッドのスタックのウォークを伴います。</span><span class="sxs-lookup"><span data-stu-id="08daf-136">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="08daf-137">非同期のウォークは、アンマネージ コード、プラットフォームの一部ではない場合は、スタックの一番上のシード呼び出し (PInvoke) 必要がありますまたは COM 呼び出しが CLR 自体でヘルパー コード。</span><span class="sxs-lookup"><span data-stu-id="08daf-137">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="08daf-138">たとえば、・ イン タイム (JIT) コンパイル中またはガベージ コレクションを実行するコードは、ヘルパー コードです。</span><span class="sxs-lookup"><span data-stu-id="08daf-138">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="08daf-139">直接対象のスレッドを中断、シードを取得し、自分で、最上位に表示されるまでにマネージ フレーム スタックを走査します。</span><span class="sxs-lookup"><span data-stu-id="08daf-139">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="08daf-140">対象のスレッドが中断された後は、対象のスレッドの現在のレジスタのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="08daf-140">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="08daf-141">次に、レジスタのコンテキストが呼び出すことによってアンマネージ コードを指すかどうかを決定[icorprofilerinfo::getfunctionfromip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) : 返された場合、 `FunctionID` 0 に等しい、フレームがアンマネージ コードです。</span><span class="sxs-lookup"><span data-stu-id="08daf-141">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="08daf-142">ここで、最初のマネージ フレームに到達し、そのフレームのレジスタのコンテキストに基づき、シード コンテキストを計算するまでは、スタックを走査します。</span><span class="sxs-lookup"><span data-stu-id="08daf-142">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="08daf-143">呼び出す`DoStackSnapshot`非同期スタック ウォークを開始する、シード コンテキストを使用します。</span><span class="sxs-lookup"><span data-stu-id="08daf-143">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="08daf-144">シードを指定しない場合`DoStackSnapshot`スタックの一番上でマネージ フレームをスキップする場合があり、その結果が提供するスタック ウォークが不完全です。</span><span class="sxs-lookup"><span data-stu-id="08daf-144">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="08daf-145">シードを指定する場合は、JIT コンパイルまたはネイティブ イメージ ジェネレーター (Ngen.exe) を指している必要があります-生成されたコードです。それ以外の場合、 `DoStackSnapshot` CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX、エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="08daf-145">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="08daf-146">非同期のスタック ウォークはデッドロックが発生するまたはアクセス違反が次のガイドラインに従わない場合、簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="08daf-146">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
-   <span data-ttu-id="08daf-147">直接のスレッドを中断する場合は、マネージ コードを実行しないが、スレッドのみが別のスレッドを中断できますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="08daf-147">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
-   <span data-ttu-id="08daf-148">常にブロック、 [icorprofilercallback::threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)そのスレッドのスタック ウォークが完了するまでのコールバック。</span><span class="sxs-lookup"><span data-stu-id="08daf-148">Always block in your [ICorProfilerCallback::ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
-   <span data-ttu-id="08daf-149">プロファイラーは、ガベージ コレクションをトリガーできる CLR 関数を呼び出すときに、ロックを保持しないでください。</span><span class="sxs-lookup"><span data-stu-id="08daf-149">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="08daf-150">つまり、所有元のスレッドがガベージ コレクションをトリガーする呼び出しを行う場合は、ロックを保持しないでください。</span><span class="sxs-lookup"><span data-stu-id="08daf-150">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="08daf-151">デッドロックの危険性を呼び出す場合`DoStackSnapshot`別の対象のスレッドのスタックを走査できるように、プロファイラーが作成したスレッドからです。</span><span class="sxs-lookup"><span data-stu-id="08daf-151">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="08daf-152">最初に作成したスレッドが特定`ICorProfilerInfo*`メソッド (含む`DoStackSnapshot`)、CLR がスレッドごと、そのスレッドで CLR 固有の初期化を実行します。</span><span class="sxs-lookup"><span data-stu-id="08daf-152">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="08daf-153">プロファイラーが対象のスレッドがスタック ウォークをしようとしてを中断している場合、このスレッドごとの初期化を実行するために必要なロックを所有する対象のスレッドが発生した場合、デッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="08daf-153">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="08daf-154">このデッドロックを避けるために最初の呼び出しを行う`DoStackSnapshot`に段階的に、プロファイラーが作成したスレッドから別のスレッドは対象まず対象のスレッドを中断しないようにします。</span><span class="sxs-lookup"><span data-stu-id="08daf-154">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="08daf-155">この初期の呼び出しにより、デッドロックなしスレッドごとの初期化を完了できるようにします。</span><span class="sxs-lookup"><span data-stu-id="08daf-155">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="08daf-156">場合`DoStackSnapshot`が成功し、レポートには、少なくとも 1 つのフレームでは、その後、ことが、対象のスレッドと呼び出しを中断するプロファイラーが作成したスレッドの安全な`DoStackSnapshot`その対象のスレッドのスタック ウォークをします。</span><span class="sxs-lookup"><span data-stu-id="08daf-156">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08daf-157">必要条件</span><span class="sxs-lookup"><span data-stu-id="08daf-157">Requirements</span></span>  
 <span data-ttu-id="08daf-158">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="08daf-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08daf-159">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08daf-159">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08daf-160">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08daf-160">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08daf-161">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08daf-161">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08daf-162">参照</span><span class="sxs-lookup"><span data-stu-id="08daf-162">See Also</span></span>  
 [<span data-ttu-id="08daf-163">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08daf-163">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="08daf-164">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08daf-164">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
