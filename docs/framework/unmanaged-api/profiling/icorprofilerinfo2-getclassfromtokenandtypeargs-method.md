---
title: "ICorProfilerInfo2::GetClassFromTokenAndTypeArgs メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 332be5616ac11fc89df8c8d54aa5c0cbc49491ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="a023b-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs メソッド</span><span class="sxs-lookup"><span data-stu-id="a023b-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="a023b-103">取得、`ClassID`指定したメタデータ トークンを使用して、型の`ClassID`いずれかの値が引数を入力します。</span><span class="sxs-lookup"><span data-stu-id="a023b-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a023b-104">構文</span><span class="sxs-lookup"><span data-stu-id="a023b-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a023b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a023b-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a023b-106">[in]型が含まれているモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="a023b-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="a023b-107">[in]`mdTypeDef`型を参照するメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="a023b-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="a023b-108">[in]指定した型の型パラメーターの数。</span><span class="sxs-lookup"><span data-stu-id="a023b-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="a023b-109">この値は、非ジェネリック型の 0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a023b-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="a023b-110">[in]配列`ClassID`値、それぞれが、型の引数。</span><span class="sxs-lookup"><span data-stu-id="a023b-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="a023b-111">値`typeArgs`場合は NULL にすることができます`cTypeArgs`は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="a023b-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="a023b-112">[out]ポインター、`ClassID`指定した型のです。</span><span class="sxs-lookup"><span data-stu-id="a023b-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a023b-113">コメント</span><span class="sxs-lookup"><span data-stu-id="a023b-113">Remarks</span></span>  
 <span data-ttu-id="a023b-114">呼び出す、`GetClassFromTokenAndTypeArgs`メソッドを`mdTypeRef`の代わりに、`mdTypeDef`メタデータ トークンが予期しない結果を持つことができます。 呼び出し元を解決する必要があります、`mdTypeRef`を、`mdTypeDef`渡すときです。</span><span class="sxs-lookup"><span data-stu-id="a023b-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="a023b-115">型が既に読み込まれていない場合は、呼び出す`GetClassFromTokenAndTypeArgs`読み込みで、さまざまなコンテキストでこの操作をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="a023b-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="a023b-116">たとえば、モジュールまたはその他の型の読み込み中にこのメソッドを呼び出す可能性があります無限ループが発生するように、ランタイムが循環的に読み込みを試みます。</span><span class="sxs-lookup"><span data-stu-id="a023b-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="a023b-117">一般の使用`GetClassFromTokenAndTypeArgs`をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a023b-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="a023b-118">プロファイラーは、特定の種類のイベントに関心があるを場合格納する必要があります、`ModuleID`と`mdTypeDef`その種類、および使用の[icorprofilerinfo 2::getclassidinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)を確認するかどうか、指定された`ClassID`はの名前に、必要な型。</span><span class="sxs-lookup"><span data-stu-id="a023b-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a023b-119">要件</span><span class="sxs-lookup"><span data-stu-id="a023b-119">Requirements</span></span>  
 <span data-ttu-id="a023b-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a023b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a023b-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a023b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a023b-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a023b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a023b-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a023b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a023b-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="a023b-124">See Also</span></span>  
 [<span data-ttu-id="a023b-125">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a023b-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="a023b-126">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a023b-126">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
