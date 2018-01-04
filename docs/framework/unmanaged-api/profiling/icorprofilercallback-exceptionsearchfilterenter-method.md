---
title: "ICorProfilerCallback::ExceptionSearchFilterEnter メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchFilterEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8196b9393a96619c17fa2771e3481cd47aafd4b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="c4577-102">ICorProfilerCallback::ExceptionSearchFilterEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="c4577-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="c4577-103">例外処理の検索フェーズで、ユーザー定義の例外フィルターの実行が開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c4577-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4577-104">構文</span><span class="sxs-lookup"><span data-stu-id="c4577-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4577-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c4577-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c4577-106">[in]フィルターを含む関数の ID。</span><span class="sxs-lookup"><span data-stu-id="c4577-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4577-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="c4577-107">Requirements</span></span>  
 <span data-ttu-id="c4577-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c4577-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4577-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c4577-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4577-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4577-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4577-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4577-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4577-112">参照</span><span class="sxs-lookup"><span data-stu-id="c4577-112">See Also</span></span>  
 [<span data-ttu-id="c4577-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4577-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c4577-114">ExceptionSearchFilterLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="c4577-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
