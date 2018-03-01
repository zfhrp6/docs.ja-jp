---
title: "ICorProfilerInfo2::GetCodeInfo2 メソッド"
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
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b211ba79de7454361b44c6e9852ad6698c2e71c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="d75e8-102">ICorProfilerInfo2::GetCodeInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d75e8-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="d75e8-103">指定した `FunctionID` に関連付けられているネイティブ コードの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="d75e8-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d75e8-104">構文</span><span class="sxs-lookup"><span data-stu-id="d75e8-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d75e8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d75e8-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="d75e8-106">[in] ネイティブ コードが関連付けられている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="d75e8-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="d75e8-107">[in] `codeInfos` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d75e8-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="d75e8-108">[out]合計数へのポインター [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d75e8-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="d75e8-109">[out] 呼び出し元が提供したバッファー。</span><span class="sxs-lookup"><span data-stu-id="d75e8-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="d75e8-110">メソッドから制御が戻ると、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` 構造体の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d75e8-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d75e8-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d75e8-111">Remarks</span></span>  
 <span data-ttu-id="d75e8-112">エクステンとは Microsoft Intermediate Language (MSIL) オフセットの昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="d75e8-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="d75e8-113">`GetCodeInfo2` から制御が戻ったら、`codeInfos` バッファーのサイズが十分で、すべての `COR_PRF_CODE_INFO` 構造体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d75e8-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="d75e8-114">これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="d75e8-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="d75e8-115">`COR_PRF_CODE_INFO` 構造体のサイズによって除算された `cCodeInfos` が `pcCodeInfos` より小さい場合は、`codeInfos` バッファーの割り当てを増やし、`cCodeInfos` を新しい大きいサイズに更新した後、`GetCodeInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d75e8-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="d75e8-116">別の方法として、最初に長さ 0 の `codeInfos` バッファーを指定して `GetCodeInfo2` を呼び出すことで、適切なバッファーのサイズを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="d75e8-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d75e8-117">その後、`codeInfos` バッファーのサイズを、`pcCodeInfos` で返された値に `COR_PRF_CODE_INFO` 構造体のサイズを掛けた値に設定し、`GetCodeInfo2` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d75e8-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d75e8-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="d75e8-118">Requirements</span></span>  
 <span data-ttu-id="d75e8-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d75e8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d75e8-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d75e8-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d75e8-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d75e8-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d75e8-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d75e8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d75e8-123">参照</span><span class="sxs-lookup"><span data-stu-id="d75e8-123">See Also</span></span>  
 [<span data-ttu-id="d75e8-124">GetCodeInfo3 メソッド</span><span class="sxs-lookup"><span data-stu-id="d75e8-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)  
 [<span data-ttu-id="d75e8-125">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d75e8-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="d75e8-126">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d75e8-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d75e8-127">プロファイル</span><span class="sxs-lookup"><span data-stu-id="d75e8-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
