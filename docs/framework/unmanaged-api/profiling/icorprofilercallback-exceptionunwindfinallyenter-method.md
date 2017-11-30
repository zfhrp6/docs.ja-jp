---
title: "ICorProfilerCallback::ExceptionUnwindFinallyEnter メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec1b05e67a10f5e7b22a950d1dec24528b5c4914
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="43ce8-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="43ce8-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="43ce8-103">例外のアンワインド フェーズの処理が入ることをプロファイラーに通知、`finally`句が指定された関数に含まれています。</span><span class="sxs-lookup"><span data-stu-id="43ce8-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ce8-104">構文</span><span class="sxs-lookup"><span data-stu-id="43ce8-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43ce8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="43ce8-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="43ce8-106">[in]含む関数の ID、`finally`句。</span><span class="sxs-lookup"><span data-stu-id="43ce8-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43ce8-107">コメント</span><span class="sxs-lookup"><span data-stu-id="43ce8-107">Remarks</span></span>  
 <span data-ttu-id="43ce8-108">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="43ce8-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="43ce8-109">ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="43ce8-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="43ce8-110">このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="43ce8-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ce8-111">要件</span><span class="sxs-lookup"><span data-stu-id="43ce8-111">Requirements</span></span>  
 <span data-ttu-id="43ce8-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="43ce8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ce8-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43ce8-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43ce8-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43ce8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43ce8-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ce8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ce8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="43ce8-116">See Also</span></span>  
 [<span data-ttu-id="43ce8-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43ce8-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="43ce8-118">GetNotifiedExceptionClauseInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="43ce8-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)  
 [<span data-ttu-id="43ce8-119">ExceptionUnwindFinallyLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="43ce8-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)