---
title: ICorProfilerCallback3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc63a0a42c1da11daa5d38ecce505296a893616b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="c58c7-102">ICorProfilerCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c58c7-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="c58c7-103">共通言語ランタイム (CLR) が通信するために使用するコールバック メソッドのアタッチし、状態に関する情報をプロファイラーをデタッチを提供します。</span><span class="sxs-lookup"><span data-stu-id="c58c7-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c58c7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c58c7-104">Methods</span></span>  
  
|<span data-ttu-id="c58c7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c58c7-105">Method</span></span>|<span data-ttu-id="c58c7-106">説明</span><span class="sxs-lookup"><span data-stu-id="c58c7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c58c7-107">InitializeForAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="c58c7-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="c58c7-108">プロファイラーのアタッチ操作後の状態を初期化する機会を提供する CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c58c7-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="c58c7-109">ProfilerAttachComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="c58c7-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="c58c7-110">プロファイラーがキャッチアップ メソッドを呼び出すことができますようになりましたことを示すために CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c58c7-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="c58c7-111">ProfilerDetachSucceeded メソッド</span><span class="sxs-lookup"><span data-stu-id="c58c7-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="c58c7-112">共通言語ランタイム (CLR: Common Language Runtime) がプロファイラー DLL をアンロードしようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c58c7-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c58c7-113">コメント</span><span class="sxs-lookup"><span data-stu-id="c58c7-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c58c7-114">要件</span><span class="sxs-lookup"><span data-stu-id="c58c7-114">Requirements</span></span>  
 <span data-ttu-id="c58c7-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c58c7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c58c7-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c58c7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c58c7-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c58c7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c58c7-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c58c7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c58c7-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c58c7-119">See Also</span></span>  
 [<span data-ttu-id="c58c7-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c58c7-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c58c7-121">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c58c7-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c58c7-122">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c58c7-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="c58c7-123">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c58c7-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
