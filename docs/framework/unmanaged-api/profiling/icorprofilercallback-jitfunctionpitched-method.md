---
title: "ICorProfilerCallback::JITFunctionPitched メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITFunctionPitched
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5b14bc5735c83897e818ca2038455e0c6510e27
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="e91c8-102">ICorProfilerCallback::JITFunctionPitched メソッド</span><span class="sxs-lookup"><span data-stu-id="e91c8-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="e91c8-103">プロファイラーに通知を・ イン タイム (JIT) されている関数のコンパイルはメモリから削除されました。</span><span class="sxs-lookup"><span data-stu-id="e91c8-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91c8-104">構文</span><span class="sxs-lookup"><span data-stu-id="e91c8-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e91c8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e91c8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e91c8-106">[in]削除された関数の ID。</span><span class="sxs-lookup"><span data-stu-id="e91c8-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e91c8-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e91c8-107">Remarks</span></span>  
 <span data-ttu-id="e91c8-108">削除された関数が呼び出されると、プロファイラーは、関数が再コンパイルするとき、新しい JIT コンパイル イベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e91c8-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="e91c8-109">現時点では、共通言語ランタイム (CLR) の JIT コンパイラは削除されません関数をメモリからこのコールバックは現在使用されていませんし、プロファイラーでは受信されません。</span><span class="sxs-lookup"><span data-stu-id="e91c8-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="e91c8-110">値`functionId`が、関数が再コンパイルされるまで、無効です。</span><span class="sxs-lookup"><span data-stu-id="e91c8-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="e91c8-111">関数を再コンパイルすると、同じ`functionId`値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e91c8-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e91c8-112">要件</span><span class="sxs-lookup"><span data-stu-id="e91c8-112">Requirements</span></span>  
 <span data-ttu-id="e91c8-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e91c8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e91c8-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e91c8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e91c8-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e91c8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e91c8-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e91c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91c8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e91c8-117">See Also</span></span>  
 [<span data-ttu-id="e91c8-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e91c8-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
