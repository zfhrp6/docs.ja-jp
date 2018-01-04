---
title: "ICorProfilerCallback2::FinalizeableObjectQueued メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.FinalizeableObjectQueued
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ed9c66f7d588d855daa550031c832810b914d49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="d70d9-102">ICorProfilerCallback2::FinalizeableObjectQueued メソッド</span><span class="sxs-lookup"><span data-stu-id="d70d9-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="d70d9-103">コード プロファイラーに通知を実行するため、ファイナライザー スレッドにファイナライザーを持つオブジェクトがキューに格納されていること、`Finalize`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d70d9-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="d70d9-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d70d9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d70d9-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="d70d9-106">[in]値、 [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)ファイナライザーの側面を説明する列挙体です。</span><span class="sxs-lookup"><span data-stu-id="d70d9-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="d70d9-107">[in]キューに登録されましたが、オブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="d70d9-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70d9-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="d70d9-108">Requirements</span></span>  
 <span data-ttu-id="d70d9-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d70d9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d70d9-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d70d9-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d70d9-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d70d9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d70d9-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d70d9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70d9-113">参照</span><span class="sxs-lookup"><span data-stu-id="d70d9-113">See Also</span></span>  
 [<span data-ttu-id="d70d9-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d70d9-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d70d9-115">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d70d9-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
