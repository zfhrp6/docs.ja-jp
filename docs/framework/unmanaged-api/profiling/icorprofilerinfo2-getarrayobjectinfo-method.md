---
title: "ICorProfilerInfo2::GetArrayObjectInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetArrayObjectInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b20530081f7c9ad32f4702099abacc78e052ebd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="10973-102">ICorProfilerInfo2::GetArrayObjectInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="10973-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="10973-103">配列オブジェクトに関する詳細情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="10973-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10973-104">構文</span><span class="sxs-lookup"><span data-stu-id="10973-104">Syntax</span></span>  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10973-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10973-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="10973-106">[in]有効な配列オブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="10973-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="10973-107">[in]配列のランク (次元数)。</span><span class="sxs-lookup"><span data-stu-id="10973-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="10973-108">[out]それぞれの配列の次元のサイズを表す整数値を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="10973-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="10973-109">[out]整数を含む配列、配列の次元の下限を表すそれぞれバインドします。</span><span class="sxs-lookup"><span data-stu-id="10973-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="10973-110">[out]C++ の規約に従ってレイアウトは、配列の生バッファーのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="10973-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10973-111">コメント</span><span class="sxs-lookup"><span data-stu-id="10973-111">Remarks</span></span>  
 <span data-ttu-id="10973-112">`pDimensionSizes`と`pDimensionLowerBounds`は並列配列は、ため各配列内の同じインデックスにある要素が、同じエンティティの特性。</span><span class="sxs-lookup"><span data-stu-id="10973-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10973-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="10973-113">Requirements</span></span>  
 <span data-ttu-id="10973-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="10973-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10973-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10973-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10973-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10973-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10973-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10973-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10973-118">参照</span><span class="sxs-lookup"><span data-stu-id="10973-118">See Also</span></span>  
 [<span data-ttu-id="10973-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10973-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="10973-120">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10973-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
