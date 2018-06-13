---
title: ICorProfilerInfo2::GetThreadAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 690dbb5659ce991b7c4921fbd85c246da54eff0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453042"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="c9962-102">ICorProfilerInfo2::GetThreadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="c9962-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="c9962-103">指定したスレッドが実行されているコード、アプリケーション ドメインの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="c9962-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9962-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9962-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9962-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9962-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c9962-106">[in]スレッドを指定する ID です。</span><span class="sxs-lookup"><span data-stu-id="c9962-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="c9962-107">[out]アプリケーション ドメインの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c9962-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9962-108">要件</span><span class="sxs-lookup"><span data-stu-id="c9962-108">Requirements</span></span>  
 <span data-ttu-id="c9962-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9962-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9962-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9962-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9962-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9962-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9962-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9962-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9962-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9962-113">See Also</span></span>  
 [<span data-ttu-id="c9962-114">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9962-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c9962-115">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9962-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
