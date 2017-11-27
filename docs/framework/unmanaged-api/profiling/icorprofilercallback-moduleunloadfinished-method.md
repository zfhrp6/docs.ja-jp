---
title: "ICorProfilerCallback::ModuleUnloadFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dc97a4173e384622fefa7de528a9725b68923ff2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="9c1d6-102">ICorProfilerCallback::ModuleUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="9c1d6-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="9c1d6-103">モジュールのアンロードが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9c1d6-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c1d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c1d6-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c1d6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c1d6-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="9c1d6-106">[in]読み込まれていないモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="9c1d6-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="9c1d6-107">[in]かどうか、モジュールがアンロードされました正常を示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9c1d6-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c1d6-108">コメント</span><span class="sxs-lookup"><span data-stu-id="9c1d6-108">Remarks</span></span>  
 <span data-ttu-id="9c1d6-109">値`moduleId`後情報の要求に対して無効です、 [icorprofilercallback::moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)メソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="9c1d6-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="9c1d6-110">クラスのアンロードの一部が後に続ける可能性があります、`ModuleUnloadFinished`コールバック。</span><span class="sxs-lookup"><span data-stu-id="9c1d6-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="9c1d6-111">失敗を示す HRESULT で`hrStatus`は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="9c1d6-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9c1d6-112">ただし、成功 HRESULT で`hrStatus`のみに、モジュールのアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9c1d6-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c1d6-113">要件</span><span class="sxs-lookup"><span data-stu-id="9c1d6-113">Requirements</span></span>  
 <span data-ttu-id="9c1d6-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c1d6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c1d6-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c1d6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c1d6-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c1d6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c1d6-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c1d6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1d6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c1d6-118">See Also</span></span>  
 [<span data-ttu-id="9c1d6-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c1d6-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
