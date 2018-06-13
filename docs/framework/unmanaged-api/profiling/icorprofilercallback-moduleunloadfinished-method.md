---
title: ICorProfilerCallback::ModuleUnloadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a4637ac7466a575c94f8244168576c4a5542689
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452089"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="132de-102">ICorProfilerCallback::ModuleUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="132de-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="132de-103">モジュールのアンロードが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="132de-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="132de-104">構文</span><span class="sxs-lookup"><span data-stu-id="132de-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="132de-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="132de-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="132de-106">[in]読み込まれていないモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="132de-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="132de-107">[in]かどうか、モジュールがアンロードされました正常を示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="132de-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="132de-108">コメント</span><span class="sxs-lookup"><span data-stu-id="132de-108">Remarks</span></span>  
 <span data-ttu-id="132de-109">値`moduleId`後情報の要求に対して無効です、 [icorprofilercallback::moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)メソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="132de-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="132de-110">クラスのアンロードの一部が後に続ける可能性があります、`ModuleUnloadFinished`コールバック。</span><span class="sxs-lookup"><span data-stu-id="132de-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="132de-111">失敗を示す HRESULT で`hrStatus`は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="132de-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="132de-112">ただし、成功 HRESULT で`hrStatus`のみに、モジュールのアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="132de-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="132de-113">要件</span><span class="sxs-lookup"><span data-stu-id="132de-113">Requirements</span></span>  
 <span data-ttu-id="132de-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="132de-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="132de-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="132de-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="132de-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="132de-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="132de-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="132de-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="132de-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="132de-118">See Also</span></span>  
 [<span data-ttu-id="132de-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="132de-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
