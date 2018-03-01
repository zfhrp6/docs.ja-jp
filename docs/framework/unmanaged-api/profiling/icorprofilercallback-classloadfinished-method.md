---
title: "ICorProfilerCallback::ClassLoadFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae55325f514f9bec3efdf4764958e4b3fafd922b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="65e30-102">ICorProfilerCallback::ClassLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="65e30-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="65e30-103">クラスの読み込みが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="65e30-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e30-104">構文</span><span class="sxs-lookup"><span data-stu-id="65e30-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65e30-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65e30-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="65e30-106">[in]既に読み込まれているクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="65e30-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="65e30-107">[in]クラスが正常に読み込まれたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="65e30-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65e30-108">コメント</span><span class="sxs-lookup"><span data-stu-id="65e30-108">Remarks</span></span>  
 <span data-ttu-id="65e30-109">値`classId`まで情報の要求に対して無効です、`ClassLoadFinished`メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="65e30-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="65e30-110">クラスの読み込みの一部が後に続ける可能性があります、`ClassLoadFinished`コールバック。</span><span class="sxs-lookup"><span data-stu-id="65e30-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="65e30-111">失敗を示す HRESULT で`hrStatus`は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="65e30-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="65e30-112">ただし、成功 HRESULT で`hrStatus`のみに、クラスの読み込みの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="65e30-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65e30-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="65e30-113">Requirements</span></span>  
 <span data-ttu-id="65e30-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="65e30-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65e30-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65e30-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65e30-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65e30-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65e30-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65e30-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e30-118">参照</span><span class="sxs-lookup"><span data-stu-id="65e30-118">See Also</span></span>  
 [<span data-ttu-id="65e30-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="65e30-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="65e30-120">ClassLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="65e30-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
