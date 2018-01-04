---
title: "ICorProfilerCallback::JITInlining メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITInlining
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3990fdf1bcf76592288aac35b47b15f42cf77bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="fe4a2-102">ICorProfilerCallback::JITInlining メソッド</span><span class="sxs-lookup"><span data-stu-id="fe4a2-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="fe4a2-103">・ イン タイム (JIT) コンパイラを別の関数に沿った関数を挿入することをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe4a2-104">構文</span><span class="sxs-lookup"><span data-stu-id="fe4a2-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe4a2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe4a2-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="fe4a2-106">[in]これに関数の ID、`calleeId`関数が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="fe4a2-107">[in]挿入される関数の ID。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="fe4a2-108">[out]`true`発生; への挿入を許可する場合は、`false`です。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe4a2-109">コメント</span><span class="sxs-lookup"><span data-stu-id="fe4a2-109">Remarks</span></span>  
 <span data-ttu-id="fe4a2-110">プロファイラーを設定できます`pfShouldInline`に`false`を防ぐために、`calleeId`関数に挿入されてから、`callerId`関数。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="fe4a2-111">また、プロファイラー グローバルに無効にできますインライン挿入の COR_PRF_DISABLE_INLINING 値を使用して、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="fe4a2-112">挿入された関数をインラインでは、出入りに関するイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="fe4a2-113">したがって、プロファイラーを設定する必要があります`pfShouldInline`に`false`正確なコールグラフを生成するためにします。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="fe4a2-114">設定`pfShouldInline`に`false`インライン挿入は通常速度が向上し、挿入されたメソッドの別の JIT コンパイル イベントの数が減るため、パフォーマンスに影響されます。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe4a2-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="fe4a2-115">Requirements</span></span>  
 <span data-ttu-id="fe4a2-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fe4a2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe4a2-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe4a2-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe4a2-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe4a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe4a2-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe4a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4a2-120">参照</span><span class="sxs-lookup"><span data-stu-id="fe4a2-120">See Also</span></span>  
 [<span data-ttu-id="fe4a2-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe4a2-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
