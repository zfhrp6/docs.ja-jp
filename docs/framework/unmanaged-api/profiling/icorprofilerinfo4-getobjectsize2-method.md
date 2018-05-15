---
title: ICorProfilerInfo4::GetObjectSize2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ebbc3422f48c0c2b8ff7b807228c63fbb35dd7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="e0d2b-102">ICorProfilerInfo4::GetObjectSize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="e0d2b-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="e0d2b-103">指定したオブジェクトのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="e0d2b-103">Returns the size of a specified object.</span></span> <span data-ttu-id="e0d2b-104">置換、 [icorprofilerinfo::getobjectsize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)メソッドで表現できる内容よりも大きいオブジェクトのサイズを報告することによって、`ULONG`です。</span><span class="sxs-lookup"><span data-stu-id="e0d2b-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d2b-105">構文</span><span class="sxs-lookup"><span data-stu-id="e0d2b-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0d2b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e0d2b-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="e0d2b-107">[in]オブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="e0d2b-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="e0d2b-108">[out]オブジェクトのサイズ (バイト) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e0d2b-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0d2b-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e0d2b-109">Remarks</span></span>  
 <span data-ttu-id="e0d2b-110">別のオブジェクトと同じ型の多くの場合、同じサイズであります。</span><span class="sxs-lookup"><span data-stu-id="e0d2b-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="e0d2b-111">ただし、配列や文字列などのいくつかの種類は、各オブジェクトのサイズが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0d2b-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0d2b-112">要件</span><span class="sxs-lookup"><span data-stu-id="e0d2b-112">Requirements</span></span>  
 <span data-ttu-id="e0d2b-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e0d2b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0d2b-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0d2b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0d2b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0d2b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0d2b-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0d2b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d2b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0d2b-117">See Also</span></span>  
 [<span data-ttu-id="e0d2b-118">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0d2b-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
