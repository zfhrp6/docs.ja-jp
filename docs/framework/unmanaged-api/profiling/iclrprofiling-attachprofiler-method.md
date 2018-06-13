---
title: ICLRProfiling::AttachProfiler メソッド
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52e3498b54f90e7d9d1d1d79ae0817cca511af4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459506"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="db65f-102">ICLRProfiling::AttachProfiler メソッド</span><span class="sxs-lookup"><span data-stu-id="db65f-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="db65f-103">指定されたプロファイラーを、指定されたプロセスにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="db65f-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db65f-104">構文</span><span class="sxs-lookup"><span data-stu-id="db65f-104">Syntax</span></span>  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db65f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db65f-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="db65f-106">[in] プロファイラーをアタッチする必要があるプロセスのプロセス ID。</span><span class="sxs-lookup"><span data-stu-id="db65f-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="db65f-107">64 ビット コンピューターでは、プロファイル対象のプロセスのビット数は `AttachProfiler` を呼び出しているトリガー プロセスのビット数に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db65f-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="db65f-108">`AttachProfiler` が呼び出されるユーザー アカウントに管理特権がある場合は、システム上のどのプロセスもターゲット プロセスにすることができます。</span><span class="sxs-lookup"><span data-stu-id="db65f-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="db65f-109">それ以外の場合は、同じユーザー アカウントがターゲット プロセスを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="db65f-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="db65f-110">[in] `AttachProfiler` が完了するまでの時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="db65f-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="db65f-111">トリガー プロセスは、特定のプロファイラーが初期化を完了するために十分であることがわかっているタイムアウトを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="db65f-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="db65f-112">[in] 読み込まれるプロファイラーの CLSID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="db65f-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="db65f-113">トリガー プロセスでは、`AttachProfiler` が戻った後にこのメモリを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="db65f-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="db65f-114">[in] 読み込まれるプロファイラーの DLL ファイルへの完全パス。</span><span class="sxs-lookup"><span data-stu-id="db65f-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="db65f-115">この文字列に含める文字数は、null 終端文字も含めて 260 文字以内にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="db65f-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="db65f-116">`wszProfilerPath` が null または空の文字列である場合、共通言語ランタイム (CLR: Common Language Runtime) は、`pClsidProfiler` が示す CLSID のレジストリ内を探してプロファイラーの DLL ファイルの場所を見つけることを試みます。</span><span class="sxs-lookup"><span data-stu-id="db65f-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="db65f-117">[in]によってプロファイラーに渡されるデータへのポインター、 [icorprofilercallback 3::initializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="db65f-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="db65f-118">トリガー プロセスでは、`AttachProfiler` が戻った後にこのメモリを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="db65f-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="db65f-119">`pvClientData` が null の場合、`cbClientData` を 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="db65f-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="db65f-120">[in] `pvClientData` がポイントするデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="db65f-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db65f-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="db65f-121">Return Value</span></span>  
 <span data-ttu-id="db65f-122">このメソッドは、次の特定の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="db65f-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="db65f-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db65f-123">HRESULT</span></span>|<span data-ttu-id="db65f-124">説明</span><span class="sxs-lookup"><span data-stu-id="db65f-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db65f-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="db65f-125">S_OK</span></span>|<span data-ttu-id="db65f-126">指定されたプロファイラーは、正常にターゲット プロセスにアタッチされました。</span><span class="sxs-lookup"><span data-stu-id="db65f-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="db65f-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="db65f-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="db65f-128">アクティブなプロファイラーまたはターゲット プロセスにアタッチされているプロファイラーが既に存在します。</span><span class="sxs-lookup"><span data-stu-id="db65f-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="db65f-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="db65f-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="db65f-130">指定されたプロファイラーはアタッチをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="db65f-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="db65f-131">トリガー プロセスは、別のプロファイラーへのアタッチを試みる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="db65f-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="db65f-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="db65f-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="db65f-133">ターゲット プロセスのバージョンが、`AttachProfiler` を呼び出している現在のプロセスと互換性がないため、プロファイラーのアタッチを要求できません。</span><span class="sxs-lookup"><span data-stu-id="db65f-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="db65f-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="db65f-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="db65f-135">トリガー プロセスのユーザーは、ターゲット プロセスにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="db65f-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="db65f-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="db65f-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="db65f-137">トリガー プロセスのユーザーは、プロファイラーを特定のターゲット プロセスにアタッチするために必要な特権を持っていません。</span><span class="sxs-lookup"><span data-stu-id="db65f-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="db65f-138">アプリケーション イベント ログには、詳細情報が含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="db65f-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="db65f-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="db65f-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="db65f-140">ターゲット プロセスとやり取りする際にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="db65f-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="db65f-141">これは、通常、ターゲット プロセスがシャットダウンしていた場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="db65f-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="db65f-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="db65f-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="db65f-143">ターゲット プロセスは存在していないか、アタッチをサポートする CLR を実行していません。</span><span class="sxs-lookup"><span data-stu-id="db65f-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="db65f-144">これは、ランタイムの列挙型メソッドの呼び出し以降に CLR がアンロードされたことを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="db65f-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="db65f-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="db65f-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="db65f-146">プロファイラーの読み込みを開始せずにタイムアウトの時間切れになりました。</span><span class="sxs-lookup"><span data-stu-id="db65f-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="db65f-147">アタッチ操作は再試行できます。</span><span class="sxs-lookup"><span data-stu-id="db65f-147">You can retry the attach operation.</span></span> <span data-ttu-id="db65f-148">ターゲット プロセスのファイナライザーがタイムアウト値よりも長く実行されると、タイムアウトが発生します。</span><span class="sxs-lookup"><span data-stu-id="db65f-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="db65f-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="db65f-149">E_INVALIDARG</span></span>|<span data-ttu-id="db65f-150">1 つ以上のパラメーターの値が無効です。</span><span class="sxs-lookup"><span data-stu-id="db65f-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="db65f-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db65f-151">E_FAIL</span></span>|<span data-ttu-id="db65f-152">他の何らかの未指定のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="db65f-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="db65f-153">その他のエラー コード</span><span class="sxs-lookup"><span data-stu-id="db65f-153">Other error codes</span></span>|<span data-ttu-id="db65f-154">場合、プロファイラーの[icorprofilercallback 3::initializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)メソッドが、失敗を示す HRESULT を返す`AttachProfiler`同じを返します HRESULT。</span><span class="sxs-lookup"><span data-stu-id="db65f-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="db65f-155">この場合、E_NOTIMPL は CORPROF_E_PROFILER_NOT_ATTACHABLE に変換されます。</span><span class="sxs-lookup"><span data-stu-id="db65f-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db65f-156">コメント</span><span class="sxs-lookup"><span data-stu-id="db65f-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="db65f-157">メモリ管理</span><span class="sxs-lookup"><span data-stu-id="db65f-157">Memory Management</span></span>  
 <span data-ttu-id="db65f-158">COM 規則に従うと、`pvClientData` パラメーターが示すデータのメモリの割り当てと割り当て解除の責任は `AttachProfiler` の呼び出し元 (たとえば、プロファイラーの開発者が作成したトリガー コード) にあります。</span><span class="sxs-lookup"><span data-stu-id="db65f-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="db65f-159">CLR は `AttachProfiler` の呼び出しを実行するときに、`pvClientData` が示すメモリをコピーし、それを対象プロセスに送信します。</span><span class="sxs-lookup"><span data-stu-id="db65f-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="db65f-160">対象プロセス内の CLR が `pvClientData` ブロックのコピーを受信すると、`InitializeForAttach` メソッドを通じてプロファイラーにそのブロックを渡してから、対象プロセスから `pvClientData` ブロックのコピーを解放します。</span><span class="sxs-lookup"><span data-stu-id="db65f-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db65f-161">要件</span><span class="sxs-lookup"><span data-stu-id="db65f-161">Requirements</span></span>  
 <span data-ttu-id="db65f-162">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="db65f-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db65f-163">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="db65f-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="db65f-164">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db65f-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db65f-165">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db65f-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db65f-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="db65f-166">See Also</span></span>  
 [<span data-ttu-id="db65f-167">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="db65f-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="db65f-168">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="db65f-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="db65f-169">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="db65f-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="db65f-170">プロファイル</span><span class="sxs-lookup"><span data-stu-id="db65f-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
