---
title: "StackSnapshotCallback 関数"
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
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32cf21fb5a76fdec4daa322d53a8eb218ae2f2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="6c0bf-102">StackSnapshotCallback 関数</span><span class="sxs-lookup"><span data-stu-id="6c0bf-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="6c0bf-103">によって開始されるスタック ウォーク中のスタックの各マネージ フレームとアンマネージのフレームの各実行に関する情報を使用してプロファイラーを提供、 [icorprofilerinfo 2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0bf-104">構文</span><span class="sxs-lookup"><span data-stu-id="6c0bf-104">Syntax</span></span>  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c0bf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6c0bf-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="6c0bf-106">[in]この値が 0 の場合は、このコールバックはアンマネージ フレーム; の実行それ以外の場合、マネージ関数の識別子、このコールバックがあるマネージ フレーム。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="6c0bf-107">[in]フレーム内のネイティブ コードの命令ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="6c0bf-108">[in]A`COR_PRF_FRAME_INFO`スタック フレームに関する情報を参照する値。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="6c0bf-109">この値は、このコールバック中にのみ使用するため有効です。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6c0bf-110">[in]サイズ、`CONTEXT`によって参照されている構造体、`context`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="6c0bf-111">[in]Win32 へのポインター`CONTEXT`このフレームの CPU の状態を表す構造です。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="6c0bf-112">`context`パラメーターは、COR_PRF_SNAPSHOT_CONTEXT フラグが渡された場合にのみ有効`ICorProfilerInfo2::DoStackSnapshot`です。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="6c0bf-113">[in]ストレートから渡されるクライアント データへのポインター`ICorProfilerInfo2::DoStackSnapshot`です。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c0bf-114">コメント</span><span class="sxs-lookup"><span data-stu-id="6c0bf-114">Remarks</span></span>  
 <span data-ttu-id="6c0bf-115">`StackSnapshotCallback`関数は、プロファイラー ライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="6c0bf-116">行われた作業の複雑さを制限する必要があります`StackSnapshotCallback`です。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="6c0bf-117">使用する場合など、`ICorProfilerInfo2::DoStackSnapshot`非同期で対象のスレッドがするロックを保持しています。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="6c0bf-118">場合内のコード`StackSnapshotCallback`、同じロックが必要です、デッドロックが発生したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="6c0bf-119">`ICorProfilerInfo2::DoStackSnapshot`メソッドの呼び出し、`StackSnapshotCallback`マネージ フレームごとに 1 回または 1 回はアンマネージ フレームの実行ごとの関数。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="6c0bf-120">場合`StackSnapshotCallback`が呼び出された、プロファイラーのアンマネージ フレームの実行、レジスタのコンテキストを使用して可能性があります (により参照されている、`context`パラメーター) をアンマネージ スタック ウォークを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="6c0bf-121">この場合は、Win32`CONTEXT`構造体が最後にプッシュされたフレーム アンマネージ フレームの実行中の CPU の状態を表します。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="6c0bf-122">ただし、Win32`CONTEXT`構造体には、すべてのレジスタの値が含まれています、フレーム ポインター レジスタ、スタック ポインター レジスタ、命令ポインター レジスタ、および (つまり、保持された) 非揮発性の値にのみ依存する必要があります整数レジスタします。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c0bf-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="6c0bf-123">Requirements</span></span>  
 <span data-ttu-id="6c0bf-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6c0bf-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0bf-125">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="6c0bf-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6c0bf-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c0bf-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c0bf-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c0bf-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0bf-128">参照</span><span class="sxs-lookup"><span data-stu-id="6c0bf-128">See Also</span></span>  
 [<span data-ttu-id="6c0bf-129">DoStackSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="6c0bf-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="6c0bf-130">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="6c0bf-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
