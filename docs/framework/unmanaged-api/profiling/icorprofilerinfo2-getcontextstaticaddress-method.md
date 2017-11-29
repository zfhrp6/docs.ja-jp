---
title: "ICorProfilerInfo2::GetContextStaticAddress メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d206ca90b2d89ead67f419f0f4511d19d8ce110
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="2612d-102">ICorProfilerInfo2::GetContextStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="2612d-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="2612d-103">指定したコンテキストのスコープ内にある指定したコンテキストの静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2612d-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2612d-104">構文</span><span class="sxs-lookup"><span data-stu-id="2612d-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2612d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2612d-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2612d-106">[in]要求されたコンテキストの静的フィールドを格納するクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="2612d-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="2612d-107">[in]要求されたコンテキストの静的フィールドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="2612d-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="2612d-108">[in]要求されたコンテキストの静的フィールドのスコープとなっているコンテキストの ID。</span><span class="sxs-lookup"><span data-stu-id="2612d-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="2612d-109">[out]指定したコンテキスト内にある静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2612d-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2612d-110">コメント</span><span class="sxs-lookup"><span data-stu-id="2612d-110">Remarks</span></span>  
 <span data-ttu-id="2612d-111">`GetContextStaticAddress`メソッドは、次のいずれかを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2612d-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="2612d-112">指定された静的フィールドに指定されたコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT です。</span><span class="sxs-lookup"><span data-stu-id="2612d-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="2612d-113">ガベージ コレクション ヒープ内で使用できるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="2612d-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="2612d-114">これらのアドレスはガベージ コレクションの後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後に無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2612d-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="2612d-115">クラスのクラスのコンス トラクターが完了するまで`GetContextStaticAddress`静的フィールドの一部は既に初期化可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE が返され、ガベージ コレクション オブジェクトをルートします。</span><span class="sxs-lookup"><span data-stu-id="2612d-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2612d-116">要件</span><span class="sxs-lookup"><span data-stu-id="2612d-116">Requirements</span></span>  
 <span data-ttu-id="2612d-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2612d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2612d-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2612d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2612d-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2612d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2612d-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2612d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2612d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="2612d-121">See Also</span></span>  
 [<span data-ttu-id="2612d-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2612d-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="2612d-123">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2612d-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
