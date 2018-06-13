---
title: ICorProfilerCallback::ExceptionThrown メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3358150754fd039d6e6107efd61c8d950fd02f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452599"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="4986f-102">ICorProfilerCallback::ExceptionThrown メソッド</span><span class="sxs-lookup"><span data-stu-id="4986f-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="4986f-103">例外がスローされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4986f-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4986f-104">この関数は、例外がマネージ コードに達した場合にのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4986f-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4986f-105">構文</span><span class="sxs-lookup"><span data-stu-id="4986f-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4986f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4986f-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="4986f-107">[in]例外をスローする原因になったオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="4986f-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4986f-108">コメント</span><span class="sxs-lookup"><span data-stu-id="4986f-108">Remarks</span></span>  
 <span data-ttu-id="4986f-109">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="4986f-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="4986f-110">ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="4986f-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="4986f-111">このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4986f-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4986f-112">要件</span><span class="sxs-lookup"><span data-stu-id="4986f-112">Requirements</span></span>  
 <span data-ttu-id="4986f-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4986f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4986f-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4986f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4986f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4986f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4986f-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4986f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4986f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4986f-117">See Also</span></span>  
 [<span data-ttu-id="4986f-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4986f-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
