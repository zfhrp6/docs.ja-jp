---
title: ICorProfilerInfo::GetCurrentThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89f7ff2c213dc510268f9e6c802813a48e870d99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453855"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="dd48f-102">ICorProfilerInfo::GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="dd48f-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="dd48f-103">マネージ スレッドである場合は、現在のスレッドの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="dd48f-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd48f-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd48f-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd48f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd48f-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="dd48f-106">[out]マネージ スレッドの返された ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dd48f-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd48f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dd48f-107">Remarks</span></span>  
 <span data-ttu-id="dd48f-108">現在のスレッドが内部ランタイム スレッドまたは他のアンマネージ スレッドの場合`GetCurrentThreadID`、HRESULT の戻り値として CORPROF_E_NOT_MANAGED_THREAD を返します、`pThreadId`パラメーターは null になります。</span><span class="sxs-lookup"><span data-stu-id="dd48f-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd48f-109">要件</span><span class="sxs-lookup"><span data-stu-id="dd48f-109">Requirements</span></span>  
 <span data-ttu-id="dd48f-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd48f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd48f-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd48f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd48f-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd48f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd48f-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd48f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd48f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd48f-114">See Also</span></span>  
 [<span data-ttu-id="dd48f-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd48f-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
