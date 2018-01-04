---
title: "ICorProfilerCallback::RuntimeThreadResumed メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeThreadResumed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94d7e46140b36d6fcce788d70cc856a6776e9f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="fd8a3-102">ICorProfilerCallback::RuntimeThreadResumed メソッド</span><span class="sxs-lookup"><span data-stu-id="fd8a3-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="fd8a3-103">指定したスレッドが中断された後に再開されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="fd8a3-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd8a3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd8a3-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="fd8a3-106">[in]再開されているスレッドの ID です。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd8a3-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="fd8a3-107">Requirements</span></span>  
 <span data-ttu-id="fd8a3-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd8a3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd8a3-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd8a3-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd8a3-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd8a3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd8a3-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd8a3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8a3-112">参照</span><span class="sxs-lookup"><span data-stu-id="fd8a3-112">See Also</span></span>  
 [<span data-ttu-id="fd8a3-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd8a3-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="fd8a3-114">RuntimeThreadSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="fd8a3-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
