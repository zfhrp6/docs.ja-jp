---
title: ICorProfilerCallback::ClassUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c30fb5d5576a7bed403f48504ead923df212de9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450376"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="8b535-102">ICorProfilerCallback::ClassUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="8b535-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="8b535-103">クラスがアンロードされることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8b535-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b535-104">構文</span><span class="sxs-lookup"><span data-stu-id="8b535-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b535-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b535-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="8b535-106">[in]モジュールはアンロードされているクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="8b535-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b535-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8b535-107">Remarks</span></span>  
 <span data-ttu-id="8b535-108">値`classId`後情報の要求に対して無効です、`ClassUnloadStarted`メソッドを返します。-これは、プロファイラーの最後のチャンスをこのクラスについての情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="8b535-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b535-109">要件</span><span class="sxs-lookup"><span data-stu-id="8b535-109">Requirements</span></span>  
 <span data-ttu-id="8b535-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8b535-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b535-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b535-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b535-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b535-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b535-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b535-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b535-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b535-114">See Also</span></span>  
 [<span data-ttu-id="8b535-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b535-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8b535-116">ClassUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="8b535-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
