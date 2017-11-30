---
title: "ICorProfilerInfo::GetILToNativeMapping メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILToNativeMapping
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8d7b248d27f9336fbc846a50e513d18f02c6aa7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="eb4c9-102">ICorProfilerInfo::GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="eb4c9-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="eb4c9-103">Microsoft Intermediate Language (MSIL) オフセットから、指定した関数に含まれるコードのネイティブ オフセットへのマップを取得します。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb4c9-104">構文</span><span class="sxs-lookup"><span data-stu-id="eb4c9-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb4c9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb4c9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="eb4c9-106">[in] コードを含む関数の ID。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="eb4c9-107">[in] `map` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="eb4c9-108">[out]使用可能な COR_DEBUG_IL_TO_NATIVE_MAP 構造体の合計数。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="eb4c9-109">[out] `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の配列。各構造体はオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="eb4c9-110">`GetILToNativeMapping` メソッドから制御が戻ると、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の一部または全部が `map` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb4c9-111">コメント</span><span class="sxs-lookup"><span data-stu-id="eb4c9-111">Remarks</span></span>  
 <span data-ttu-id="eb4c9-112">`GetILToNativeMapping` メソッドは、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="eb4c9-113">ネイティブ命令の特定の範囲がコード (たとえば、プロローグ) の特殊な領域に対応することを伝える、配列内のエントリが持つことができます、`ilOffset`フィールドの値に設定、 [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)列挙体です。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="eb4c9-114">`GetILToNativeMapping` から制御が戻ったら、`map` バッファーのサイズが十分で、すべての `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="eb4c9-115">これを行うには、`cMap` の値を `pcMap` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="eb4c9-116">`pcMap` 値 に `COR_DEBUG_IL_TO_NATIVE_MAP` 構造体のサイズを乗算した結果が `cMap` より大きい場合は、`map` バッファーの割り当てを増やし、`cMap` を新しい大きいサイズに更新した後、`GetILToNativeMapping` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="eb4c9-117">別の方法として、最初に `GetILToNativeMapping` を長さゼロの `map` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="eb4c9-118">その後、バッファーのサイズを `pcMap` で返された値に設定し、`GetILToNativeMapping` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb4c9-119">要件</span><span class="sxs-lookup"><span data-stu-id="eb4c9-119">Requirements</span></span>  
 <span data-ttu-id="eb4c9-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb4c9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb4c9-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb4c9-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb4c9-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb4c9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb4c9-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb4c9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4c9-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb4c9-124">See Also</span></span>  
 [<span data-ttu-id="eb4c9-125">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb4c9-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="eb4c9-126">GetILToNativeMapping2 メソッド</span><span class="sxs-lookup"><span data-stu-id="eb4c9-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)  
 [<span data-ttu-id="eb4c9-127">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb4c9-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="eb4c9-128">プロファイル</span><span class="sxs-lookup"><span data-stu-id="eb4c9-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
