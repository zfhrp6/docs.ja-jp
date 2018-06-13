---
title: ICorProfilerCallback::ExceptionCatcherEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8a87fb05a49c2813cf4d299c3663419be1640b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450831"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="9d210-102">ICorProfilerCallback::ExceptionCatcherEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="9d210-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="9d210-103">適切な制御が渡されることをプロファイラーに通知`catch`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="9d210-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d210-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d210-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d210-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d210-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9d210-106">[in]含む関数の識別子、`catch`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="9d210-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="9d210-107">[in]処理中の例外の識別子。</span><span class="sxs-lookup"><span data-stu-id="9d210-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d210-108">コメント</span><span class="sxs-lookup"><span data-stu-id="9d210-108">Remarks</span></span>  
 <span data-ttu-id="9d210-109">`ExceptionCatcherEnter` ・ イン タイム (JIT) コンパイラでコンパイルされたコードでキャッチ ポイントがある場合にのみ、メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9d210-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="9d210-110">アンマネージ コードで、またはランタイムの内部のコードにキャッチされる例外には、この通知は呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="9d210-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="9d210-111">`objectId`値は再度、ガベージ コレクションからオブジェクトが移動した可能性がありますので、`ExceptionThrown`通知します。</span><span class="sxs-lookup"><span data-stu-id="9d210-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="9d210-112">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="9d210-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9d210-113">ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="9d210-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9d210-114">このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9d210-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d210-115">要件</span><span class="sxs-lookup"><span data-stu-id="9d210-115">Requirements</span></span>  
 <span data-ttu-id="9d210-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d210-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d210-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d210-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d210-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d210-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d210-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d210-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d210-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d210-120">See Also</span></span>  
 [<span data-ttu-id="9d210-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d210-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9d210-122">ExceptionCatcherLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="9d210-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
