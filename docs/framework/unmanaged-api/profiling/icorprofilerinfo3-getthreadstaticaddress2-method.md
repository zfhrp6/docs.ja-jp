---
title: "ICorProfilerInfo3::GetThreadStaticAddress2 メソッド"
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
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 136b68f886899430dbfc672b8e3e534d093bc617
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="1ffe7-102">ICorProfilerInfo3::GetThreadStaticAddress2 メソッド</span><span class="sxs-lookup"><span data-stu-id="1ffe7-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="1ffe7-103">指定したスレッドおよびアプリケーション ドメインのスコープ内にある、指定したスレッド内静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffe7-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ffe7-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ffe7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ffe7-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="1ffe7-106">[in]要求されたスレッド内静的フィールドを格納するクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="1ffe7-107">[in]要求されたスレッド内静的フィールドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="1ffe7-108">[in] アプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="1ffe7-109">[in]要求された静的フィールドのスコープにあるスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="1ffe7-110">[out]指定したスレッド内静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ffe7-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1ffe7-111">Remarks</span></span>  
 <span data-ttu-id="1ffe7-112">`GetThreadStaticAddress2`メソッドは、次のいずれかを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="1ffe7-113">指定された静的フィールドに指定されたコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT です。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="1ffe7-114">ガベージ コレクション ヒープ内で使用できるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="1ffe7-115">これらのアドレスはガベージ コレクションの後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後に無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="1ffe7-116">クラスのクラスのコンス トラクターが完了するまで`GetThreadStaticAddress2`静的フィールドの一部は既に初期化可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE が返され、ガベージ コレクション オブジェクトをルートします。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="1ffe7-117">[Icorprofilerinfo 2::getthreadstaticaddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)メソッドがに似ていますが、`GetThreadStaticAddress2`メソッドは、アプリケーション ドメインの引数を受け付けられません。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ffe7-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="1ffe7-118">Requirements</span></span>  
 <span data-ttu-id="1ffe7-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ffe7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ffe7-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1ffe7-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ffe7-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ffe7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ffe7-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ffe7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffe7-123">参照</span><span class="sxs-lookup"><span data-stu-id="1ffe7-123">See Also</span></span>  
 [<span data-ttu-id="1ffe7-124">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ffe7-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="1ffe7-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ffe7-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="1ffe7-126">プロファイル</span><span class="sxs-lookup"><span data-stu-id="1ffe7-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
