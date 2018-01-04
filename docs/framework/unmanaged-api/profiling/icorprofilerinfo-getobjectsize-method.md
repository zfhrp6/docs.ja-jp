---
title: "ICorProfilerInfo::GetObjectSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetObjectSize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9425938042485c4330fe3fbc50cdabde6451b427
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="8332d-102">ICorProfilerInfo::GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="8332d-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="8332d-103">指定したオブジェクトのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="8332d-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8332d-104">構文</span><span class="sxs-lookup"><span data-stu-id="8332d-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8332d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8332d-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="8332d-106">[in]オブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="8332d-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="8332d-107">[out]オブジェクトのサイズ (バイト) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8332d-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8332d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="8332d-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8332d-109">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="8332d-109">This method is obsolete.</span></span> <span data-ttu-id="8332d-110">返します COR_E_OVERFLOW オブジェクトに対して 4 GB より大きい 64 ビット プラットフォーム上でします。</span><span class="sxs-lookup"><span data-stu-id="8332d-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="8332d-111">使用して、 [icorprofilerinfo 4::getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="8332d-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="8332d-112">別のオブジェクトと同じ型の多くの場合、同じサイズであります。</span><span class="sxs-lookup"><span data-stu-id="8332d-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="8332d-113">ただし、配列や文字列などのいくつかの種類は、各オブジェクトのサイズが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8332d-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="8332d-114">によって返されるサイズ、`GetObjectSize`メソッドでは、配置のオブジェクトがガベージ コレクション ヒープにした後に表示される埋め込みは含まれません。</span><span class="sxs-lookup"><span data-stu-id="8332d-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="8332d-115">使用する場合、`GetObjectSize`ガベージ コレクション ヒープのオブジェクトからオブジェクトを進める方法は、手動で、必要に応じて、パディングの配置を追加します。</span><span class="sxs-lookup"><span data-stu-id="8332d-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="8332d-116">32 ビット Windows で COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1、および COR_PRF_GC_GEN_2 4 バイトのアラインメントを使用し、COR_PRF_GC_LARGE_OBJECT_HEAP が 8 バイト アラインメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8332d-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="8332d-117">64 ビット Windows で、配置は常に 8 バイトです。</span><span class="sxs-lookup"><span data-stu-id="8332d-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8332d-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="8332d-118">Requirements</span></span>  
 <span data-ttu-id="8332d-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8332d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8332d-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8332d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8332d-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8332d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8332d-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8332d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8332d-123">参照</span><span class="sxs-lookup"><span data-stu-id="8332d-123">See Also</span></span>  
 [<span data-ttu-id="8332d-124">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8332d-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
