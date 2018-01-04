---
title: "ICorProfilerCallback::ThreadDestroyed メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 419a8a0797761429f41f7472d812aaebdbbf706c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="81880-102">ICorProfilerCallback::ThreadDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="81880-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="81880-103">スレッドが破棄されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="81880-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81880-104">構文</span><span class="sxs-lookup"><span data-stu-id="81880-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81880-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81880-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="81880-106">[in]破棄されているスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="81880-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81880-107">コメント</span><span class="sxs-lookup"><span data-stu-id="81880-107">Remarks</span></span>  
 <span data-ttu-id="81880-108">`threadId`値は、この呼び出しの時点では有効ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="81880-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81880-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="81880-109">Requirements</span></span>  
 <span data-ttu-id="81880-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="81880-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81880-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="81880-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="81880-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81880-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81880-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81880-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81880-114">参照</span><span class="sxs-lookup"><span data-stu-id="81880-114">See Also</span></span>  
 [<span data-ttu-id="81880-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81880-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="81880-116">ThreadCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="81880-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
