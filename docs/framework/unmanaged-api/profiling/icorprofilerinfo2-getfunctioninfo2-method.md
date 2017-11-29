---
title: "ICorProfilerInfo2::GetFunctionInfo2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b0c288b88c868bc6e324ec57b3956344f03f34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="44947-102">ICorProfilerInfo2::GetFunctionInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="44947-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="44947-103">関数の親クラス、メタデータ トークン、および型引数が存在する場合はそれぞれの `ClassID` を取得します。</span><span class="sxs-lookup"><span data-stu-id="44947-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44947-104">構文</span><span class="sxs-lookup"><span data-stu-id="44947-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44947-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="44947-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="44947-106">[in] 親クラスおよびその他の情報を取得する関数の ID。</span><span class="sxs-lookup"><span data-stu-id="44947-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="44947-107">[in] スタック フレームに関する情報を指す `COR_PRF_FRAME_INFO` 値。</span><span class="sxs-lookup"><span data-stu-id="44947-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="44947-108">[out] 関数の親クラスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="44947-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="44947-109">[out] 関数の親クラスが定義されているモジュールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="44947-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="44947-110">[out] 関数のメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="44947-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="44947-111">[in] `typeArgs` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="44947-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="44947-112">[out] `ClassID` 値の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="44947-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="44947-113">[out] `ClassID` 値の配列。各値は、関数の型引数の ID です。</span><span class="sxs-lookup"><span data-stu-id="44947-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="44947-114">このメソッドが戻るとき、使用できる `ClassID` 値の一部または全部が `typeArgs` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="44947-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44947-115">コメント</span><span class="sxs-lookup"><span data-stu-id="44947-115">Remarks</span></span>  
 <span data-ttu-id="44947-116">プロファイラー コードを呼び出すことができます[icorprofilerinfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)を取得する、[メタデータ](../../../../docs/framework/unmanaged-api/metadata/index.md)指定したモジュールのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="44947-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="44947-117">`pToken` が参照している場所に返されるメタデータ トークンを使用すると、関数のメタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="44947-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="44947-118">次の表に示すように、`pClassId` パラメーターで返されるクラス ID、および `typeArgs` パラメーターで返される型引数は、`frameInfo` パラメーターで渡される値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="44947-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="44947-119">パラメーター `frameInfo` の値。</span><span class="sxs-lookup"><span data-stu-id="44947-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="44947-120">結果</span><span class="sxs-lookup"><span data-stu-id="44947-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="44947-121">`FunctionEnter2` コールバックから取得された `COR_PRF_FRAME_INFO` 値</span><span class="sxs-lookup"><span data-stu-id="44947-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="44947-122">`pClassId` によって参照される場所に返される `ClassID` と、`typeArgs` 配列で返されるすべての型引数は正確です。</span><span class="sxs-lookup"><span data-stu-id="44947-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="44947-123">`FunctionEnter2` コールバック以外のソースから取得された `COR_PRF_FRAME_INFO`</span><span class="sxs-lookup"><span data-stu-id="44947-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="44947-124">正確な `ClassID` と型引数を特定できません。</span><span class="sxs-lookup"><span data-stu-id="44947-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="44947-125">つまり、`ClassID` は null の可能性があり、一部の型引数は <xref:System.Object> として戻る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44947-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="44947-126">0</span><span class="sxs-lookup"><span data-stu-id="44947-126">Zero</span></span>|<span data-ttu-id="44947-127">正確な `ClassID` と型引数を特定できません。</span><span class="sxs-lookup"><span data-stu-id="44947-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="44947-128">つまり、`ClassID` は null の可能性があり、一部の型引数は <xref:System.Object> として戻る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44947-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="44947-129">`GetFunctionInfo2` から制御が戻ったら、`typeArgs` バッファーのサイズが十分で、すべての `ClassID` 値を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44947-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="44947-130">これを行うには、`pcTypeArgs` が指している値を `cTypeArgs` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="44947-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="44947-131">`pcTypeArgs` の指す値が、`ClassID` 値のサイズで除算された `cTypeArgs` の値より大きい場合は、`pcTypeArgs` バッファーの割り当てを増やし、`cTypeArgs` を新しい大きいサイズに更新して、`GetFunctionInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="44947-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="44947-132">別の方法として、最初に長さ 0 の `pcTypeArgs` バッファーで `GetFunctionInfo2` を呼び出すことで、適切なバッファーのサイズを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="44947-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="44947-133">その後、バッファーのサイズを `pcTypeArgs` に返された値 (`ClassID` 値のサイズで除算された値) に設定し、`GetFunctionInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="44947-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44947-134">要件</span><span class="sxs-lookup"><span data-stu-id="44947-134">Requirements</span></span>  
 <span data-ttu-id="44947-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="44947-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44947-136">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44947-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44947-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44947-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44947-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44947-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44947-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="44947-139">See Also</span></span>  
 [<span data-ttu-id="44947-140">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44947-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="44947-141">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44947-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="44947-142">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="44947-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="44947-143">プロファイル</span><span class="sxs-lookup"><span data-stu-id="44947-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
