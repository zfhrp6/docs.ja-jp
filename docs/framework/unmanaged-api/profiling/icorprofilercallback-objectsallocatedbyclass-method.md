---
title: "ICorProfilerCallback::ObjectsAllocatedByClass メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectsAllocatedByClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 28c0ff537a5b2133bdeb1db8aeadf5545d8dfd0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="d4df3-102">ICorProfilerCallback::ObjectsAllocatedByClass メソッド</span><span class="sxs-lookup"><span data-stu-id="d4df3-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="d4df3-103">最新のガベージ コレクションの後に作成された指定した各クラスのインスタンスの数をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d4df3-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4df3-104">構文</span><span class="sxs-lookup"><span data-stu-id="d4df3-104">Syntax</span></span>  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4df3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4df3-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="d4df3-106">[in]サイズ、`classIds`と`cObjects`配列。</span><span class="sxs-lookup"><span data-stu-id="d4df3-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="d4df3-107">[in]クラスの各 ID が指定されているクラスに 1 つまたは複数のインスタンス Id の配列。</span><span class="sxs-lookup"><span data-stu-id="d4df3-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="d4df3-108">[in]各整数値に対応するクラスのインスタンスの数が指定されている整数の配列、`classIds`配列。</span><span class="sxs-lookup"><span data-stu-id="d4df3-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4df3-109">コメント</span><span class="sxs-lookup"><span data-stu-id="d4df3-109">Remarks</span></span>  
 <span data-ttu-id="d4df3-110">`classIds`と`cObjects`配列は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="d4df3-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="d4df3-111">たとえば、`classIds[i]`と`cObjects[i]`同じクラスを参照します。</span><span class="sxs-lookup"><span data-stu-id="d4df3-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="d4df3-112">前のガベージ コレクションの後、クラスのインスタンスが作成されていません、このクラスは省略されます。</span><span class="sxs-lookup"><span data-stu-id="d4df3-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="d4df3-113">`ObjectsAllocatedByClass`コールバックは、大きなオブジェクト ヒープに割り当てられたオブジェクトをレポートしません。</span><span class="sxs-lookup"><span data-stu-id="d4df3-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="d4df3-114">によって、報告される`ObjectsAllocatedByClass`は推定値のみです。</span><span class="sxs-lookup"><span data-stu-id="d4df3-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="d4df3-115">正確な数は、使用[icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4df3-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="d4df3-116">`classIds`場合、配列が 1 つまたは複数の null エントリを含めることは、対応する`cObjects`配列には、アンロードしている型。</span><span class="sxs-lookup"><span data-stu-id="d4df3-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4df3-117">要件</span><span class="sxs-lookup"><span data-stu-id="d4df3-117">Requirements</span></span>  
 <span data-ttu-id="d4df3-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4df3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4df3-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4df3-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4df3-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4df3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4df3-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4df3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4df3-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4df3-122">See Also</span></span>  
 [<span data-ttu-id="d4df3-123">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4df3-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
