---
title: "ICorProfilerInfo2::GetThreadStaticAddress メソッド"
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
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1de945d2e6e0dd1ce3fa2da99e265bc304d4f4fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="7f8b1-102">ICorProfilerInfo2::GetThreadStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="7f8b1-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="7f8b1-103">指定したスレッドのスコープ内にある指定したスレッド内静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f8b1-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f8b1-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f8b1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f8b1-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="7f8b1-106">[in]要求されたスレッド内静的フィールドを格納するクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="7f8b1-107">[in]要求されたスレッド内静的フィールドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="7f8b1-108">[in]要求された静的フィールドのスコープにあるスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="7f8b1-109">[out]指定したスレッド内静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f8b1-110">コメント</span><span class="sxs-lookup"><span data-stu-id="7f8b1-110">Remarks</span></span>  
 <span data-ttu-id="7f8b1-111">`GetThreadStaticAddress`メソッドは、次のいずれかを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="7f8b1-112">指定された静的フィールドに指定されたコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT です。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="7f8b1-113">ガベージ コレクション ヒープ内で使用できるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="7f8b1-114">これらのアドレスが無効になり、ガベージ コレクション後にその後、ガベージ コレクションのプロファイラーが有効であるは想定しないでください。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="7f8b1-115">クラスのクラスのコンス トラクターが完了するまで`GetThreadStaticAddress`静的フィールドの一部は既に初期化可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE が返され、ガベージ コレクション オブジェクトをルートします。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f8b1-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="7f8b1-116">Requirements</span></span>  
 <span data-ttu-id="7f8b1-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f8b1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f8b1-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f8b1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f8b1-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f8b1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f8b1-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f8b1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f8b1-121">参照</span><span class="sxs-lookup"><span data-stu-id="7f8b1-121">See Also</span></span>  
 [<span data-ttu-id="7f8b1-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f8b1-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="7f8b1-123">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f8b1-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
