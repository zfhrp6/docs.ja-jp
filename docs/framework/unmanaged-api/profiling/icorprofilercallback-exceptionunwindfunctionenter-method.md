---
title: "ICorProfilerCallback::ExceptionUnwindFunctionEnter メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc41dc95776ca31178153402d2e145a3d2c13bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="dfcf2-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="dfcf2-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="dfcf2-103">関数をアンワインドする例外処理のアンワインド フェーズが開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="dfcf2-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfcf2-104">構文</span><span class="sxs-lookup"><span data-stu-id="dfcf2-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfcf2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dfcf2-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="dfcf2-106">[in]展開される関数の ID です。</span><span class="sxs-lookup"><span data-stu-id="dfcf2-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfcf2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dfcf2-107">Remarks</span></span>  
 <span data-ttu-id="dfcf2-108">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="dfcf2-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="dfcf2-109">ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="dfcf2-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="dfcf2-110">このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dfcf2-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfcf2-111">要件</span><span class="sxs-lookup"><span data-stu-id="dfcf2-111">Requirements</span></span>  
 <span data-ttu-id="dfcf2-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dfcf2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfcf2-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dfcf2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dfcf2-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfcf2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfcf2-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfcf2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfcf2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfcf2-116">See Also</span></span>  
 [<span data-ttu-id="dfcf2-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dfcf2-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dfcf2-118">ExceptionUnwindFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="dfcf2-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
