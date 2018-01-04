---
title: "ICorProfilerInfo::GetCurrentThreadID メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCurrentThreadID
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efa0bcef1acb7f1a8d89390757c25a5015f4daa7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="29607-102">ICorProfilerInfo::GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="29607-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="29607-103">マネージ スレッドである場合は、現在のスレッドの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="29607-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29607-104">構文</span><span class="sxs-lookup"><span data-stu-id="29607-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29607-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29607-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="29607-106">[out]マネージ スレッドの返された ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="29607-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29607-107">コメント</span><span class="sxs-lookup"><span data-stu-id="29607-107">Remarks</span></span>  
 <span data-ttu-id="29607-108">現在のスレッドが内部ランタイム スレッドまたは他のアンマネージ スレッドの場合`GetCurrentThreadID`、HRESULT の戻り値として CORPROF_E_NOT_MANAGED_THREAD を返します、`pThreadId`パラメーターは null になります。</span><span class="sxs-lookup"><span data-stu-id="29607-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29607-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="29607-109">Requirements</span></span>  
 <span data-ttu-id="29607-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="29607-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29607-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29607-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29607-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29607-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29607-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29607-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29607-114">参照</span><span class="sxs-lookup"><span data-stu-id="29607-114">See Also</span></span>  
 [<span data-ttu-id="29607-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29607-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
