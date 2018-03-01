---
title: "ICorProfilerCallback::ExceptionSearchCatcherFound メソッド"
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
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc226b6102c50b118a4b13f9cd25700dd1ca7301
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="b450b-102">ICorProfilerCallback::ExceptionSearchCatcherFound メソッド</span><span class="sxs-lookup"><span data-stu-id="b450b-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="b450b-103">例外処理の検索フェーズでスローされた例外のハンドラーが見つかったことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b450b-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b450b-104">構文</span><span class="sxs-lookup"><span data-stu-id="b450b-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b450b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b450b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b450b-106">[in]例外ハンドラーを含む関数の ID。</span><span class="sxs-lookup"><span data-stu-id="b450b-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b450b-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="b450b-107">Requirements</span></span>  
 <span data-ttu-id="b450b-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b450b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b450b-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b450b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b450b-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b450b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b450b-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b450b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b450b-112">参照</span><span class="sxs-lookup"><span data-stu-id="b450b-112">See Also</span></span>  
 [<span data-ttu-id="b450b-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b450b-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
