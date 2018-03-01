---
title: "ICorProfilerInfo2::GetClassIDInfo2 メソッド"
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
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0348462cdbff14486b31e1878f06b7565b47182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="95e65-102">ICorProfilerInfo2::GetClassIDInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="95e65-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="95e65-103">親モジュールとメタデータのトークンを取得、指定したクラスの汎用的な定義を開く、`ClassID`その親クラスの`ClassID`存在する場合、クラスの各型引数。</span><span class="sxs-lookup"><span data-stu-id="95e65-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e65-104">構文</span><span class="sxs-lookup"><span data-stu-id="95e65-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95e65-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="95e65-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="95e65-106">[in] 情報が取得されるクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="95e65-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="95e65-107">[out]指定したクラスの汎用的な定義を開くの親モジュールの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="95e65-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="95e65-108">[out]指定したクラスの汎用的な定義を開くのメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="95e65-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="95e65-109">[out] 親クラスの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="95e65-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="95e65-110">[in] `typeArgs` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="95e65-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="95e65-111">[out] 使用できる要素の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="95e65-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="95e65-112">[out] `ClassID` 値の配列。各値は、クラスの型引数の ID を表します。</span><span class="sxs-lookup"><span data-stu-id="95e65-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="95e65-113">このメソッドが戻るとき、使用できる `ClassID` 値の一部またはすべてが `typeArgs` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="95e65-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95e65-114">コメント</span><span class="sxs-lookup"><span data-stu-id="95e65-114">Remarks</span></span>  
 <span data-ttu-id="95e65-115">`GetClassIDInfo2`メソッドがに似ていますが、 [icorprofilerinfo::getclassidinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)メソッドが、`GetClassIDInfo2`ジェネリック型に関する追加情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="95e65-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="95e65-116">プロファイラー コードを呼び出すことができます[icorprofilerinfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)を取得する、[メタデータ](../../../../docs/framework/unmanaged-api/metadata/index.md)指定したモジュールのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="95e65-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="95e65-117">`pTypeDefToken` によって参照される場所に返されるメタデータ トークンを使用すると、クラスのメタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="95e65-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="95e65-118">`GetClassIDInfo2` から制御が戻ったら、`typeArgs` バッファーのサイズが十分で、すべての `ClassID` 値を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95e65-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="95e65-119">これを行うには、`pcNumTypeArgs` が指している値を `cNumTypeArgs` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="95e65-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="95e65-120">`pcNumTypeArgs` が指している値が `cNumTypeArgs` の値より大きい場合は、`typeArgs` バッファーの割り当てを増やし、`cNumTypeArgs` を新しい大きいサイズに更新して、`GetClassIDInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="95e65-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="95e65-121">別の方法として、最初に長さ 0 の `typeArgs` バッファーで `GetClassIDInfo2` を呼び出すことで、適切なバッファーのサイズを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="95e65-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="95e65-122">その後、`typeArgs` バッファーのサイズを `pcNumTypeArgs` に返された値に設定し、`GetClassIDInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="95e65-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95e65-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="95e65-123">Requirements</span></span>  
 <span data-ttu-id="95e65-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="95e65-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95e65-125">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95e65-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95e65-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95e65-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95e65-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95e65-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e65-128">参照</span><span class="sxs-lookup"><span data-stu-id="95e65-128">See Also</span></span>  
 [<span data-ttu-id="95e65-129">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="95e65-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="95e65-130">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="95e65-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="95e65-131">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="95e65-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="95e65-132">プロファイル</span><span class="sxs-lookup"><span data-stu-id="95e65-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
