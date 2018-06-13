---
title: ICorProfilerInfo::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acb4d67f41b1434fe8052a74e976907f24fecd31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453578"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="c2773-102">ICorProfilerInfo::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="c2773-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="c2773-103">指定したスレッドに関連付けられているコンテキスト id を取得します。</span><span class="sxs-lookup"><span data-stu-id="c2773-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2773-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2773-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2773-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2773-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c2773-106">[in]スレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="c2773-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="c2773-107">[out]指定したスレッドに関連付けられているコンテキストの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c2773-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="c2773-108">それに関連付けられているコンテキストのスレッドがない場合は、この関数は CORPROF_E_DATAINCOMPLETE を返します。</span><span class="sxs-lookup"><span data-stu-id="c2773-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2773-109">要件</span><span class="sxs-lookup"><span data-stu-id="c2773-109">Requirements</span></span>  
 <span data-ttu-id="c2773-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2773-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2773-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2773-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2773-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2773-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2773-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2773-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2773-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2773-114">See Also</span></span>  
 [<span data-ttu-id="c2773-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2773-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
