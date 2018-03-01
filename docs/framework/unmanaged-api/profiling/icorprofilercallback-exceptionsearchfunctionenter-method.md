---
title: "ICorProfilerCallback::ExceptionSearchFunctionEnter メソッド"
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
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d410d6ef47dfb0ad33c2a6a03f80d05810182a3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="2b6f2-102">ICorProfilerCallback::ExceptionSearchFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="2b6f2-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="2b6f2-103">例外処理の検索フェーズが現在の例外のハンドラーを検索する関数の検索を開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2b6f2-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6f2-104">構文</span><span class="sxs-lookup"><span data-stu-id="2b6f2-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b6f2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b6f2-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2b6f2-106">[in]入力されている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="2b6f2-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b6f2-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="2b6f2-107">Requirements</span></span>  
 <span data-ttu-id="2b6f2-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b6f2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b6f2-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b6f2-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b6f2-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b6f2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b6f2-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b6f2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6f2-112">参照</span><span class="sxs-lookup"><span data-stu-id="2b6f2-112">See Also</span></span>  
 [<span data-ttu-id="2b6f2-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b6f2-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="2b6f2-114">ExceptionSearchFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="2b6f2-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
