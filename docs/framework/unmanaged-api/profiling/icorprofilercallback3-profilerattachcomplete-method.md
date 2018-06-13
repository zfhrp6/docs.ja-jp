---
title: ICorProfilerCallback3::ProfilerAttachComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8397900e2dafb69807417090cbb30c85dd884c59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454379"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="c80a4-102">ICorProfilerCallback3::ProfilerAttachComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="c80a4-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="c80a4-103">によって、共通言語ランタイム (CLR)、プロファイラーを呼び出すことができますようになりましたことを示すために呼び出される、 [icorprofilerinfo 3::enumjitedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)と[icorprofilerinfo 3::enummodules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)キャッチアップ メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c80a4-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c80a4-104">構文</span><span class="sxs-lookup"><span data-stu-id="c80a4-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c80a4-105">コメント</span><span class="sxs-lookup"><span data-stu-id="c80a4-105">Remarks</span></span>  
 <span data-ttu-id="c80a4-106">`ProfilerAttachComplete`コールバックが後に発行された、 [icorprofilercallback 3::initializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c80a4-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="c80a4-107">これは、次のことを示します。</span><span class="sxs-lookup"><span data-stu-id="c80a4-107">It indicates the following:</span></span>  
  
-   <span data-ttu-id="c80a4-108">`InitializeForAttach` でプロファイラーによって要求されたコールバックがアクティブ化されました。</span><span class="sxs-lookup"><span data-stu-id="c80a4-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
-   <span data-ttu-id="c80a4-109">プロファイラーは、通知されないことを心配せずに、関連付けられた ID でキャッチアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c80a4-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="c80a4-110">CLR はこのコールバックからの戻り値を無視します。</span><span class="sxs-lookup"><span data-stu-id="c80a4-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c80a4-111">要件</span><span class="sxs-lookup"><span data-stu-id="c80a4-111">Requirements</span></span>  
 <span data-ttu-id="c80a4-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c80a4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c80a4-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c80a4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c80a4-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c80a4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c80a4-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c80a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c80a4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c80a4-116">See Also</span></span>  
 [<span data-ttu-id="c80a4-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c80a4-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c80a4-118">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c80a4-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="c80a4-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c80a4-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c80a4-120">プロファイル</span><span class="sxs-lookup"><span data-stu-id="c80a4-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
