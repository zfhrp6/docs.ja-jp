---
title: "GetIdentityAuthority 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: GetIdentityAuthority
helpviewer_keywords: GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fab6fa7c8e58dcd2fdece05572242230847f62f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="2b88a-102">GetIdentityAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="2b88a-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="2b88a-103">ポインターを取得、 [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)コード オブジェクトのキーを管理するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="2b88a-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b88a-104">構文</span><span class="sxs-lookup"><span data-stu-id="2b88a-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b88a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b88a-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="2b88a-106">[out]返された`IIdentityAuthority`ポインター。</span><span class="sxs-lookup"><span data-stu-id="2b88a-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b88a-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="2b88a-107">Requirements</span></span>  
 <span data-ttu-id="2b88a-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b88a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b88a-109">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="2b88a-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="2b88a-110">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b88a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b88a-111">参照</span><span class="sxs-lookup"><span data-stu-id="2b88a-111">See Also</span></span>  
 [<span data-ttu-id="2b88a-112">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b88a-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 [<span data-ttu-id="2b88a-113">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="2b88a-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
