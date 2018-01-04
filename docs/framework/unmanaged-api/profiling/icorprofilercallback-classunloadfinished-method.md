---
title: "ICorProfilerCallback::ClassUnloadFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9801113e23474fa0aae461d356e4aa57a203bd6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="0cae3-102">ICorProfilerCallback::ClassUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="0cae3-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="0cae3-103">クラスのアンロードが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0cae3-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cae3-104">構文</span><span class="sxs-lookup"><span data-stu-id="0cae3-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0cae3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0cae3-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="0cae3-106">[in]アンロードされたクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="0cae3-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="0cae3-107">[in]かどうか、クラスがアンロードされました正常を示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="0cae3-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cae3-108">コメント</span><span class="sxs-lookup"><span data-stu-id="0cae3-108">Remarks</span></span>  
 <span data-ttu-id="0cae3-109">クラスのアンロードの一部が後に続ける可能性があります、`ClassUnloadFinished`コールバック。</span><span class="sxs-lookup"><span data-stu-id="0cae3-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="0cae3-110">失敗を示す HRESULT で`hrStatus`は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="0cae3-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="0cae3-111">ただし、成功 HRESULT で`hrStatus`のみのクラスをアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="0cae3-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cae3-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="0cae3-112">Requirements</span></span>  
 <span data-ttu-id="0cae3-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0cae3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cae3-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0cae3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0cae3-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cae3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cae3-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cae3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cae3-117">参照</span><span class="sxs-lookup"><span data-stu-id="0cae3-117">See Also</span></span>  
 [<span data-ttu-id="0cae3-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0cae3-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="0cae3-119">ClassUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="0cae3-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
