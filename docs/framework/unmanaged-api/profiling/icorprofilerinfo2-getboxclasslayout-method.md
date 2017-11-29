---
title: "ICorProfilerInfo2::GetBoxClassLayout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetBoxClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c11013781a4fc8f627dac97894ff9ef02bfda51c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="5536b-102">ICorProfilerInfo2::GetBoxClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="5536b-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="5536b-103">指定した値の型が配置されているがボックス化されるときに情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="5536b-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5536b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5536b-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5536b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5536b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5536b-106">[in]ボックス化された値型を記述するクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="5536b-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="5536b-107">[out]値型のボックス化されたオブジェクト ID のポインターを基準とした、オフセットを示す整数。</span><span class="sxs-lookup"><span data-stu-id="5536b-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5536b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5536b-108">Remarks</span></span>  
 <span data-ttu-id="5536b-109">`pBufferOffset`値は、値型のボックス内の場所。</span><span class="sxs-lookup"><span data-stu-id="5536b-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="5536b-110">後に`pBufferOffset`が適用されるオブジェクトの値を解釈するボックス化されたオブジェクトに値型のクラスのレイアウトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5536b-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5536b-111">要件</span><span class="sxs-lookup"><span data-stu-id="5536b-111">Requirements</span></span>  
 <span data-ttu-id="5536b-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5536b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5536b-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5536b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5536b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5536b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5536b-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5536b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5536b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5536b-116">See Also</span></span>  
 [<span data-ttu-id="5536b-117">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5536b-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="5536b-118">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5536b-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
