---
title: "ICorProfilerInfo2::GetAppDomainStaticAddress メソッド"
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
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fad6cccc3992f001780bf8bd1a4c879dc6aa754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="02ac2-102">ICorProfilerInfo2::GetAppDomainStaticAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="02ac2-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="02ac2-103">指定されたアプリケーション ドメインのスコープ内にある指定されたアプリケーション ドメインの静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="02ac2-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ac2-104">構文</span><span class="sxs-lookup"><span data-stu-id="02ac2-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02ac2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="02ac2-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="02ac2-106">[in]要求されたアプリケーション ドメインの静的フィールドを格納するクラスのクラス ID。</span><span class="sxs-lookup"><span data-stu-id="02ac2-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="02ac2-107">[in]要求されたアプリケーション ドメインの静的フィールドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="02ac2-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="02ac2-108">[in]要求された静的フィールドのスコープとなっているアプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="02ac2-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="02ac2-109">[out]指定したアプリケーション ドメイン内にある静的フィールドのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="02ac2-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02ac2-110">コメント</span><span class="sxs-lookup"><span data-stu-id="02ac2-110">Remarks</span></span>  
 <span data-ttu-id="02ac2-111">`GetAppDomainStaticAddress`メソッドは、次のいずれかを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="02ac2-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="02ac2-112">指定された静的フィールドに指定されたコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT です。</span><span class="sxs-lookup"><span data-stu-id="02ac2-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="02ac2-113">ガベージ コレクション ヒープ内で使用できるオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="02ac2-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="02ac2-114">これらのアドレスはガベージ コレクションの後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後に無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="02ac2-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="02ac2-115">クラスのクラスのコンス トラクターが完了するまで`GetAppDomainStaticAddress`静的フィールドの一部は既に初期化可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE が返され、ガベージ コレクション オブジェクトをルートします。</span><span class="sxs-lookup"><span data-stu-id="02ac2-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02ac2-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="02ac2-116">Requirements</span></span>  
 <span data-ttu-id="02ac2-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="02ac2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02ac2-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02ac2-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02ac2-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02ac2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02ac2-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02ac2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ac2-121">参照</span><span class="sxs-lookup"><span data-stu-id="02ac2-121">See Also</span></span>  
 [<span data-ttu-id="02ac2-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02ac2-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="02ac2-123">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02ac2-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
