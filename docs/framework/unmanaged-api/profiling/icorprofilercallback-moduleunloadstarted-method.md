---
title: "ICorProfilerCallback::ModuleUnloadStarted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 069e47ad3d1dd9459b7344b1af1a2ad6d32305ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="dce6c-102">ICorProfilerCallback::ModuleUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="dce6c-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="dce6c-103">モジュールがアンロードされることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="dce6c-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce6c-104">構文</span><span class="sxs-lookup"><span data-stu-id="dce6c-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="dce6c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dce6c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="dce6c-106">[in]モジュールはアンロードされているモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="dce6c-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dce6c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dce6c-107">Remarks</span></span>  
 <span data-ttu-id="dce6c-108">値`moduleId`後情報の要求に対して無効です、`ModuleUnloadStarted`メソッドを返します。-これは、プロファイラーの最後のチャンスこのモジュールに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="dce6c-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dce6c-109">要件</span><span class="sxs-lookup"><span data-stu-id="dce6c-109">Requirements</span></span>  
 <span data-ttu-id="dce6c-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dce6c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dce6c-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dce6c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dce6c-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dce6c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dce6c-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dce6c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce6c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="dce6c-114">See Also</span></span>  
 [<span data-ttu-id="dce6c-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dce6c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dce6c-116">ModuleUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="dce6c-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
