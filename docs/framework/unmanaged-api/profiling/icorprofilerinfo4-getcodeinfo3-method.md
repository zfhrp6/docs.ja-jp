---
title: "ICorProfilerInfo4::GetCodeInfo3 メソッド"
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
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b669714774ecfccad436f064350569d27ef13883
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="9f582-102">ICorProfilerInfo4::GetCodeInfo3 メソッド</span><span class="sxs-lookup"><span data-stu-id="9f582-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="9f582-103">指定した関数の JIT 再コンパイル バージョンに関連付けられているネイティブ コードの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f582-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f582-104">構文</span><span class="sxs-lookup"><span data-stu-id="9f582-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f582-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f582-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="9f582-106">[in] ネイティブ コードが関連付けられている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="9f582-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="9f582-107">[in] JIT 再コンパイルされた関数のID。</span><span class="sxs-lookup"><span data-stu-id="9f582-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="9f582-108">[in] `codeInfos` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="9f582-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="9f582-109">[out]合計数へのポインター [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f582-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="9f582-110">[out] 呼び出し元が提供したバッファー。</span><span class="sxs-lookup"><span data-stu-id="9f582-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="9f582-111">メソッドから制御が戻ると、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` 構造体の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9f582-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f582-112">コメント</span><span class="sxs-lookup"><span data-stu-id="9f582-112">Remarks</span></span>  
 <span data-ttu-id="9f582-113">`GetCodeInfo3`メソッドは[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)を指定した IP アドレスを含む関数の JIT 再コンパイルされた ID を取得できる点を除いて、します。</span><span class="sxs-lookup"><span data-stu-id="9f582-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f582-114">`GetCodeInfo3`一方、ガベージ コレクションをトリガーできます[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)は表示されません。</span><span class="sxs-lookup"><span data-stu-id="9f582-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="9f582-115">詳細については、次を参照してください。、 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9f582-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="9f582-116">エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="9f582-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="9f582-117">後に`GetCodeInfo3`が返されることを確認する必要があります、`codeInfos`バッファーがすべて格納するのに十分な大きさ、 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="9f582-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="9f582-118">これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="9f582-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="9f582-119">場合`cCodeInfos`のサイズで除算し、 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造がより小さい`pcCodeInfos`、割り当てを増やし`codeInfos`更新、バッファーに保持`cCodeInfos`呼び出しと新しい大きいサイズで`GetCodeInfo3`もう一度です。</span><span class="sxs-lookup"><span data-stu-id="9f582-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="9f582-120">別の方法として、最初に長さ 0 の `codeInfos` バッファーで `GetCodeInfo3` を呼び出すことで、適切なバッファーのサイズを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="9f582-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9f582-121">設定できます、`codeInfos`バッファー サイズに返される値に`pcCodeInfos`のサイズを掛けた、 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造、および呼び出し`GetCodeInfo3`もう一度です。</span><span class="sxs-lookup"><span data-stu-id="9f582-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f582-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="9f582-122">Requirements</span></span>  
 <span data-ttu-id="9f582-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f582-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f582-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9f582-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f582-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f582-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f582-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f582-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f582-127">参照</span><span class="sxs-lookup"><span data-stu-id="9f582-127">See Also</span></span>  
 [<span data-ttu-id="9f582-128">GetCodeInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="9f582-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
 [<span data-ttu-id="9f582-129">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f582-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="9f582-130">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f582-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9f582-131">プロファイル</span><span class="sxs-lookup"><span data-stu-id="9f582-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
