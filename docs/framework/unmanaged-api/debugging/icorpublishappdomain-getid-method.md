---
title: "ICorPublishAppDomain::GetID メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomain.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08d6146c6188e23f0846f51e88484d7f1544aff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="1b1f7-102">ICorPublishAppDomain::GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="1b1f7-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="1b1f7-103">この一意の識別子を取得[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="1b1f7-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1f7-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b1f7-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b1f7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b1f7-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="1b1f7-106">[out]アプリケーション ドメインの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b1f7-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b1f7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1b1f7-107">Remarks</span></span>  
 <span data-ttu-id="1b1f7-108">識別子は、格納しているプロセスのスコープでのみ一意です。</span><span class="sxs-lookup"><span data-stu-id="1b1f7-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1f7-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="1b1f7-109">Requirements</span></span>  
 <span data-ttu-id="1b1f7-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1b1f7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1f7-111">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="1b1f7-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1b1f7-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b1f7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1f7-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1f7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1f7-114">参照</span><span class="sxs-lookup"><span data-stu-id="1b1f7-114">See Also</span></span>  
 [<span data-ttu-id="1b1f7-115">ICorPublishAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b1f7-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
