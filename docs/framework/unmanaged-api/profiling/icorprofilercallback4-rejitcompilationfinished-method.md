---
title: ICorProfilerCallback4::ReJITCompilationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cf2e1be735150dfb006e2274c79c25649d0271d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="8538b-102">ICorProfilerCallback4::ReJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="8538b-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="8538b-103">・ イン タイム (JIT) コンパイラが関数を再コンパイルを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8538b-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8538b-104">構文</span><span class="sxs-lookup"><span data-stu-id="8538b-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8538b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8538b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8538b-106">[in]再コンパイルされた関数の ID。</span><span class="sxs-lookup"><span data-stu-id="8538b-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="8538b-107">[in] JIT 再コンパイルされた関数のID。</span><span class="sxs-lookup"><span data-stu-id="8538b-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="8538b-108">[in]JIT 再コンパイルが成功したかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="8538b-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="8538b-109">[in]`true`ブロックことにより、ランタイムでこのコールバックから戻るには、呼び出し元のスレッドの待機を示すために`false`をブロックしていないに影響すること、ランタイムの動作を示します。</span><span class="sxs-lookup"><span data-stu-id="8538b-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="8538b-110">値`true`、実行時に問題が発生しませんが、プロファイルの結果に影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="8538b-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8538b-111">要件</span><span class="sxs-lookup"><span data-stu-id="8538b-111">Requirements</span></span>  
 <span data-ttu-id="8538b-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8538b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8538b-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8538b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8538b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8538b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8538b-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8538b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8538b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8538b-116">See Also</span></span>  
 [<span data-ttu-id="8538b-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8538b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8538b-118">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8538b-118">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="8538b-119">JITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="8538b-119">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [<span data-ttu-id="8538b-120">ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="8538b-120">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
