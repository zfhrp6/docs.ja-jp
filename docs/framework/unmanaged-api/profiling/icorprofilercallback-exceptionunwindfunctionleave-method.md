---
title: "ICorProfilerCallback::ExceptionUnwindFunctionLeave メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e420d27fa1bf122b794489b00853555a7005e69e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="95a9c-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="95a9c-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="95a9c-103">例外処理のアンワインド フェーズの関数のアンワインドが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="95a9c-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a9c-104">構文</span><span class="sxs-lookup"><span data-stu-id="95a9c-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="95a9c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="95a9c-105">Remarks</span></span>  
 <span data-ttu-id="95a9c-106">ときに、`ExceptionUnwindFunctionLeave`メソッドが呼び出されると、関数のインスタンスとその履歴データは、スタックから削除されます。</span><span class="sxs-lookup"><span data-stu-id="95a9c-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="95a9c-107">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、この呼び出し中にブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="95a9c-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="95a9c-108">ここでプロファイラー ブロックされ、ガベージ コレクションが実行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="95a9c-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="95a9c-109">また、この呼び出し中に、プロファイラーを呼び出してはならないにマネージ コードまたは任意の方法で管理されているメモリ割り当てが発生します。</span><span class="sxs-lookup"><span data-stu-id="95a9c-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a9c-110">要件</span><span class="sxs-lookup"><span data-stu-id="95a9c-110">Requirements</span></span>  
 <span data-ttu-id="95a9c-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="95a9c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a9c-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95a9c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95a9c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95a9c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95a9c-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a9c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a9c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="95a9c-115">See Also</span></span>  
 [<span data-ttu-id="95a9c-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="95a9c-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="95a9c-117">ExceptionUnwindFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="95a9c-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
