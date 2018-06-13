---
title: ICorProfilerInfo2::GetContextStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d787e3eae59218c46a95c327a0f93502c3833d9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456236"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="e7b56-102">ICorProfilerInfo2::GetContextStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="e7b56-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="e7b56-103">指定したコンテキストのスコープ内にある指定したコンテキストの静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e7b56-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b56-104">構文</span><span class="sxs-lookup"><span data-stu-id="e7b56-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7b56-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7b56-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e7b56-106">[in]要求されたコンテキストの静的フィールドを格納するクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="e7b56-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e7b56-107">[in]要求されたコンテキストの静的フィールドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="e7b56-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="e7b56-108">[in]要求されたコンテキストの静的フィールドのスコープとなっているコンテキストの ID。</span><span class="sxs-lookup"><span data-stu-id="e7b56-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e7b56-109">[out]指定したコンテキスト内にある静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e7b56-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7b56-110">コメント</span><span class="sxs-lookup"><span data-stu-id="e7b56-110">Remarks</span></span>  
 <span data-ttu-id="e7b56-111">`GetContextStaticAddress`メソッドは、次のいずれかを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7b56-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="e7b56-112">指定された静的フィールドに指定されたコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT です。</span><span class="sxs-lookup"><span data-stu-id="e7b56-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="e7b56-113">ガベージ コレクション ヒープ内で使用できるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="e7b56-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e7b56-114">これらのアドレスはガベージ コレクションの後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後に無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7b56-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e7b56-115">クラスのクラスのコンス トラクターが完了するまで`GetContextStaticAddress`静的フィールドの一部は既に初期化可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE が返され、ガベージ コレクション オブジェクトをルートします。</span><span class="sxs-lookup"><span data-stu-id="e7b56-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b56-116">要件</span><span class="sxs-lookup"><span data-stu-id="e7b56-116">Requirements</span></span>  
 <span data-ttu-id="e7b56-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e7b56-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b56-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7b56-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7b56-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7b56-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7b56-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b56-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b56-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7b56-121">See Also</span></span>  
 [<span data-ttu-id="e7b56-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7b56-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e7b56-123">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7b56-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
