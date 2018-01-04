---
title: "ICorProfilerInfo4::InitializeCurrentThread メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f3c261068b38861dca2633a490e46d9f44371d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="6b5a1-102">ICorProfilerInfo4::InitializeCurrentThread メソッド</span><span class="sxs-lookup"><span data-stu-id="6b5a1-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="6b5a1-103">後続のプロファイラー API は、デッドロックを回避するため、同じスレッドで呼び出しの前に、現在のスレッドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="6b5a1-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b5a1-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b5a1-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b5a1-105">コメント</span><span class="sxs-lookup"><span data-stu-id="6b5a1-105">Remarks</span></span>  
 <span data-ttu-id="6b5a1-106">呼び出すことをお勧め`InitializeCurrentThread`API が存在するときは、プロファイラーを呼び出す任意のスレッドでスレッドを中断します。</span><span class="sxs-lookup"><span data-stu-id="6b5a1-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="6b5a1-107">このメソッドは、通常サンプリング プロファイラーを呼び出す独自のスレッドを作成して使用、 [icorprofilerinfo 2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)スタック行き場メソッドで対象のスレッドを中断している間はについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6b5a1-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="6b5a1-108">呼び出して`InitializeCurrentThread`プロファイラーが CLR をそれ以外の場合、最初の呼び出し中に実行するスレッドあたりの遅延初期化を確認ときに、プロファイラーでは、まずサンプリング スレッドを作成した後`DoStackSnapshot`他のスレッドがない場合に安全に発生することができますようになりました中断されています。</span><span class="sxs-lookup"><span data-stu-id="6b5a1-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b5a1-109">`InitializeCurrentThread`ロックを実行し、デッドロックが発生するタスクを完了するには、事前に初期化します。</span><span class="sxs-lookup"><span data-stu-id="6b5a1-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="6b5a1-110">呼び出す`InitializeCurrentThread`中断されたスレッドが存在しない場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="6b5a1-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b5a1-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="6b5a1-111">Requirements</span></span>  
 <span data-ttu-id="6b5a1-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b5a1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b5a1-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b5a1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b5a1-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b5a1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b5a1-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b5a1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b5a1-116">参照</span><span class="sxs-lookup"><span data-stu-id="6b5a1-116">See Also</span></span>  
 [<span data-ttu-id="6b5a1-117">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b5a1-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="6b5a1-118">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b5a1-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6b5a1-119">プロファイル</span><span class="sxs-lookup"><span data-stu-id="6b5a1-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
