---
title: ICorProfilerCallback::ExceptionOSHandlerLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53c71914d8938067ceb5d580d42ffe7d7d8dc1df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450666"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="b6e62-102">ICorProfilerCallback::ExceptionOSHandlerLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="b6e62-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="b6e62-103">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="b6e62-103">Not implemented.</span></span> <span data-ttu-id="b6e62-104">アンマネージ例外情報を必要とするプロファイラーには、他の手段では、この情報を入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6e62-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e62-105">構文</span><span class="sxs-lookup"><span data-stu-id="b6e62-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b6e62-106">要件</span><span class="sxs-lookup"><span data-stu-id="b6e62-106">Requirements</span></span>  
 <span data-ttu-id="b6e62-107">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6e62-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6e62-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6e62-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6e62-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6e62-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6e62-110">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6e62-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e62-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6e62-111">See Also</span></span>  
 [<span data-ttu-id="b6e62-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6e62-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
