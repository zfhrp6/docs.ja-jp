---
title: "ICorProfilerCallback::ExceptionOSHandlerLeave メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionOSHandlerLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 98596fd640437639ee3d5ffad4bce8503f5f5e44
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="05b02-102">ICorProfilerCallback::ExceptionOSHandlerLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="05b02-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="05b02-103">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="05b02-103">Not implemented.</span></span> <span data-ttu-id="05b02-104">アンマネージ例外情報を必要とするプロファイラーには、他の手段では、この情報を入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05b02-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b02-105">構文</span><span class="sxs-lookup"><span data-stu-id="05b02-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="05b02-106">要件</span><span class="sxs-lookup"><span data-stu-id="05b02-106">Requirements</span></span>  
 <span data-ttu-id="05b02-107">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="05b02-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05b02-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05b02-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05b02-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05b02-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05b02-110">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05b02-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b02-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="05b02-111">See Also</span></span>  
 [<span data-ttu-id="05b02-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05b02-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
