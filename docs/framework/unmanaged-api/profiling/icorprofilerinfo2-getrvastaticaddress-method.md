---
title: ICorProfilerInfo2::GetRVAStaticAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ee12131cfa323d4426ab06ea31be4a8dd7b4583
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455466"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="f637d-102">ICorProfilerInfo2::GetRVAStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="f637d-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="f637d-103">指定された相対仮想アドレス (RVA) の静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f637d-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f637d-104">構文</span><span class="sxs-lookup"><span data-stu-id="f637d-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f637d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f637d-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="f637d-106">[in]要求された RVA 静的フィールドを格納するクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="f637d-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="f637d-107">[in]要求された RVA 静的フィールドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="f637d-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="f637d-108">[out]RVA 静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f637d-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f637d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f637d-109">Remarks</span></span>  
 <span data-ttu-id="f637d-110">`GetRVAStaticAddress`メソッドは、次のいずれかを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f637d-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="f637d-111">指定された静的フィールドに指定されたコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT です。</span><span class="sxs-lookup"><span data-stu-id="f637d-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="f637d-112">ガベージ コレクション ヒープ内で使用できるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="f637d-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="f637d-113">これらのアドレスはガベージ コレクションの後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後に無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f637d-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="f637d-114">クラスのクラスのコンス トラクターが完了するまで`GetRVAStaticAddress`は静的フィールドの一部は既に初期化し、ガベージ コレクション オブジェクトをルートする可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE を返します。</span><span class="sxs-lookup"><span data-stu-id="f637d-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f637d-115">要件</span><span class="sxs-lookup"><span data-stu-id="f637d-115">Requirements</span></span>  
 <span data-ttu-id="f637d-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f637d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f637d-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f637d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f637d-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f637d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f637d-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f637d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f637d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f637d-120">See Also</span></span>  
 [<span data-ttu-id="f637d-121">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f637d-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="f637d-122">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f637d-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
