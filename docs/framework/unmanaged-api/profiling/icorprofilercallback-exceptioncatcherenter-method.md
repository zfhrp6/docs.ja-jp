---
title: "ICorProfilerCallback::ExceptionCatcherEnter メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCatcherEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1605fdca3f5aa13ce4e29c0ff2fb42383512e6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="80459-102">ICorProfilerCallback::ExceptionCatcherEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="80459-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="80459-103">適切な制御が渡されることをプロファイラーに通知`catch`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="80459-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80459-104">構文</span><span class="sxs-lookup"><span data-stu-id="80459-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80459-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="80459-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="80459-106">[in]含む関数の識別子、`catch`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="80459-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="80459-107">[in]処理中の例外の識別子。</span><span class="sxs-lookup"><span data-stu-id="80459-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80459-108">コメント</span><span class="sxs-lookup"><span data-stu-id="80459-108">Remarks</span></span>  
 <span data-ttu-id="80459-109">`ExceptionCatcherEnter` ・ イン タイム (JIT) コンパイラでコンパイルされたコードでキャッチ ポイントがある場合にのみ、メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="80459-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="80459-110">アンマネージ コードで、またはランタイムの内部のコードにキャッチされる例外には、この通知は呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="80459-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="80459-111">`objectId`値は再度、ガベージ コレクションからオブジェクトが移動した可能性がありますので、`ExceptionThrown`通知します。</span><span class="sxs-lookup"><span data-stu-id="80459-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="80459-112">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="80459-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="80459-113">ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="80459-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="80459-114">このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="80459-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80459-115">要件</span><span class="sxs-lookup"><span data-stu-id="80459-115">Requirements</span></span>  
 <span data-ttu-id="80459-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="80459-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80459-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80459-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80459-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80459-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80459-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80459-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80459-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="80459-120">See Also</span></span>  
 [<span data-ttu-id="80459-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80459-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="80459-122">ExceptionCatcherLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="80459-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
