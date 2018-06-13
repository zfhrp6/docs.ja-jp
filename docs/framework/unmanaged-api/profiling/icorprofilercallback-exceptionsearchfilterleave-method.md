---
title: ICorProfilerCallback::ExceptionSearchFilterLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13de3470e70635243aed78ac603cebc841c8fa59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451299"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="4ed52-102">ICorProfilerCallback::ExceptionSearchFilterLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="4ed52-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="4ed52-103">実行するユーザーのフィルターをだけ完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4ed52-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed52-104">構文</span><span class="sxs-lookup"><span data-stu-id="4ed52-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="4ed52-105">要件</span><span class="sxs-lookup"><span data-stu-id="4ed52-105">Requirements</span></span>  
 <span data-ttu-id="4ed52-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4ed52-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ed52-107">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ed52-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ed52-108">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ed52-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ed52-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ed52-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed52-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ed52-110">See Also</span></span>  
 [<span data-ttu-id="4ed52-111">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ed52-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4ed52-112">ExceptionSearchFilterEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="4ed52-112">ExceptionSearchFilterEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)
