---
title: "ICorProfilerCallback::ExceptionUnwindFinallyLeave メソッド"
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
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 969bc0723929dffd16b3119a9c9b74499f35b0e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="d8aa0-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="d8aa0-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="d8aa0-103">例外のアンワインド フェーズの処理状態になっていることをプロファイラーに通知する`finally`句。</span><span class="sxs-lookup"><span data-stu-id="d8aa0-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8aa0-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8aa0-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d8aa0-105">コメント</span><span class="sxs-lookup"><span data-stu-id="d8aa0-105">Remarks</span></span>  
 <span data-ttu-id="d8aa0-106">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、この呼び出し中にブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="d8aa0-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="d8aa0-107">ここでプロファイラー ブロックされ、ガベージ コレクションが実行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="d8aa0-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="d8aa0-108">また、この呼び出し中に、プロファイラーを呼び出してはならないにマネージ コードまたは任意の方法で管理されているメモリ割り当てが発生します。</span><span class="sxs-lookup"><span data-stu-id="d8aa0-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8aa0-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="d8aa0-109">Requirements</span></span>  
 <span data-ttu-id="d8aa0-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8aa0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8aa0-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8aa0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8aa0-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8aa0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8aa0-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8aa0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8aa0-114">参照</span><span class="sxs-lookup"><span data-stu-id="d8aa0-114">See Also</span></span>  
 [<span data-ttu-id="d8aa0-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8aa0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d8aa0-116">ExceptionUnwindFinallyEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="d8aa0-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
