---
title: ICorProfilerCallback::FunctionUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e28aef4916d06218953236e3b29e19c68822bd6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451189"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="815d5-102">ICorProfilerCallback::FunctionUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="815d5-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="815d5-103">関数のアンロードをランタイムが開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="815d5-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815d5-104">構文</span><span class="sxs-lookup"><span data-stu-id="815d5-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="815d5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="815d5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="815d5-106">[in]モジュールはアンロードされている関数の ID です。</span><span class="sxs-lookup"><span data-stu-id="815d5-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="815d5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="815d5-107">Remarks</span></span>  
 <span data-ttu-id="815d5-108">値、`functionId`このメソッドが呼び出し元に返された後にパラメーターが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="815d5-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="815d5-109">要件</span><span class="sxs-lookup"><span data-stu-id="815d5-109">Requirements</span></span>  
 <span data-ttu-id="815d5-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="815d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815d5-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="815d5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="815d5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="815d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="815d5-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="815d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815d5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="815d5-114">See Also</span></span>  
 [<span data-ttu-id="815d5-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="815d5-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
