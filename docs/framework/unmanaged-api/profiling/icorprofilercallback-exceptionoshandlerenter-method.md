---
title: ICorProfilerCallback::ExceptionOSHandlerEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2dc7c22ee075f347604864d8bee1a4e871da616
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451767"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="78494-102">ICorProfilerCallback::ExceptionOSHandlerEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="78494-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="78494-103">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="78494-103">Not implemented.</span></span> <span data-ttu-id="78494-104">アンマネージ例外情報を必要とするプロファイラーには、他の手段では、この情報を入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78494-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78494-105">構文</span><span class="sxs-lookup"><span data-stu-id="78494-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="78494-106">要件</span><span class="sxs-lookup"><span data-stu-id="78494-106">Requirements</span></span>  
 <span data-ttu-id="78494-107">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78494-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78494-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78494-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78494-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78494-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78494-110">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78494-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78494-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="78494-111">See Also</span></span>  
 [<span data-ttu-id="78494-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78494-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
