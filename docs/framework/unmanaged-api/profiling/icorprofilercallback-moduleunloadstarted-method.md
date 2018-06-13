---
title: ICorProfilerCallback::ModuleUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c509606995a0ddb00a8b586ce8b8cd54b7694cd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452511"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="7aed4-102">ICorProfilerCallback::ModuleUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="7aed4-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="7aed4-103">モジュールがアンロードされることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7aed4-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aed4-104">構文</span><span class="sxs-lookup"><span data-stu-id="7aed4-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="7aed4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7aed4-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7aed4-106">[in]モジュールはアンロードされているモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="7aed4-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7aed4-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7aed4-107">Remarks</span></span>  
 <span data-ttu-id="7aed4-108">値`moduleId`後情報の要求に対して無効です、`ModuleUnloadStarted`メソッドを返します。-これは、プロファイラーの最後のチャンスこのモジュールに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="7aed4-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aed4-109">要件</span><span class="sxs-lookup"><span data-stu-id="7aed4-109">Requirements</span></span>  
 <span data-ttu-id="7aed4-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7aed4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aed4-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7aed4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7aed4-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7aed4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aed4-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aed4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aed4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7aed4-114">See Also</span></span>  
 [<span data-ttu-id="7aed4-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7aed4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="7aed4-116">ModuleUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="7aed4-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
