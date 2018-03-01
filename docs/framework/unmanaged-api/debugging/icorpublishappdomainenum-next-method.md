---
title: "ICorPublishAppDomainEnum::Next メソッド"
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
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c9823c0e4a471a398285c5960f3ce7bfc60fb23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="32fbe-102">ICorPublishAppDomainEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="32fbe-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="32fbe-103">プロセスでは、現在の位置から現在存在しているアプリケーション ドメインの指定した数を取得します。</span><span class="sxs-lookup"><span data-stu-id="32fbe-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32fbe-104">構文</span><span class="sxs-lookup"><span data-stu-id="32fbe-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32fbe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="32fbe-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="32fbe-106">[in]取得する要素の数。</span><span class="sxs-lookup"><span data-stu-id="32fbe-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="32fbe-107">[out]配列へのポインターを取得[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)アプリケーション ドメインを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="32fbe-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="32fbe-108">[out]アプリケーション ドメインの数へのポインターが実際に返されます。</span><span class="sxs-lookup"><span data-stu-id="32fbe-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="32fbe-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="32fbe-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32fbe-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="32fbe-110">Requirements</span></span>  
 <span data-ttu-id="32fbe-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="32fbe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32fbe-112">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="32fbe-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="32fbe-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32fbe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32fbe-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32fbe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fbe-115">参照</span><span class="sxs-lookup"><span data-stu-id="32fbe-115">See Also</span></span>  
 [<span data-ttu-id="32fbe-116">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32fbe-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
