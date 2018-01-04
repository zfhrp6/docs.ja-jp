---
title: "ICorProfilerObjectEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Next
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfeec7c3ee2038b77549e53b10534d817b667687
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="c6ba5-102">ICorProfilerObjectEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="c6ba5-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="c6ba5-103">列挙子の現在の位置からのオブジェクトのシーケンシャル コレクションから指定された数の隣接するオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="c6ba5-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ba5-104">構文</span><span class="sxs-lookup"><span data-stu-id="c6ba5-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6ba5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6ba5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c6ba5-106">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="c6ba5-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="c6ba5-107">[out]配列`ObjectID`取得したオブジェクトを表す値です。</span><span class="sxs-lookup"><span data-stu-id="c6ba5-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c6ba5-108">[out] `objects` 配列で実際に返されるモジュールの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c6ba5-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ba5-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="c6ba5-109">Requirements</span></span>  
 <span data-ttu-id="c6ba5-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6ba5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ba5-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c6ba5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6ba5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6ba5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6ba5-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ba5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ba5-114">参照</span><span class="sxs-lookup"><span data-stu-id="c6ba5-114">See Also</span></span>  
 [<span data-ttu-id="c6ba5-115">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6ba5-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
