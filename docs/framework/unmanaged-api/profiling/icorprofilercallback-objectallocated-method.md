---
title: ICorProfilerCallback::ObjectAllocated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7d62b1b6031f6ebdd5327626f42de38b18b3fa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452050"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="d8143-102">ICorProfilerCallback::ObjectAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="d8143-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="d8143-103">オブジェクトのヒープ内のメモリを割り当てられているプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d8143-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8143-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8143-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8143-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8143-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="d8143-106">[in]メモリが割り当てられたオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="d8143-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="d8143-107">[in]オブジェクトがインスタンス クラスの ID。</span><span class="sxs-lookup"><span data-stu-id="d8143-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8143-108">コメント</span><span class="sxs-lookup"><span data-stu-id="d8143-108">Remarks</span></span>  
 <span data-ttu-id="d8143-109">`ObjectedAllocated`スタックまたはアンマネージ メモリの割り当てのメソッドは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="d8143-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="d8143-110">`classId`パラメーターがまだ読み込まれていないマネージ コード内のクラスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="d8143-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="d8143-111">プロファイラーはそのクラスのクラス ロード コールバックの受信後すぐに、`ObjectAllocated`コールバック。</span><span class="sxs-lookup"><span data-stu-id="d8143-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8143-112">要件</span><span class="sxs-lookup"><span data-stu-id="d8143-112">Requirements</span></span>  
 <span data-ttu-id="d8143-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8143-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8143-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8143-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8143-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8143-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8143-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8143-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8143-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8143-117">See Also</span></span>  
 [<span data-ttu-id="d8143-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8143-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d8143-119">ClassLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="d8143-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)  
 [<span data-ttu-id="d8143-120">ClassLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="d8143-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
