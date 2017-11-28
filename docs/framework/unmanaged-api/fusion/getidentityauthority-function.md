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
ms.openlocfilehash: 1490efdc00c4f928d17bf172eecd5a3bed824193
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="e328a-102">GetIdentityAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="e328a-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="e328a-103">ポインターを取得、 [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)コード オブジェクトのキーを管理するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="e328a-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e328a-104">構文</span><span class="sxs-lookup"><span data-stu-id="e328a-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e328a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e328a-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="e328a-106">[out]返された`IIdentityAuthority`ポインター。</span><span class="sxs-lookup"><span data-stu-id="e328a-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e328a-107">要件</span><span class="sxs-lookup"><span data-stu-id="e328a-107">Requirements</span></span>  
 <span data-ttu-id="e328a-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e328a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e328a-109">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e328a-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e328a-110">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e328a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e328a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="e328a-111">See Also</span></span>  
 [<span data-ttu-id="e328a-112">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e328a-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 [<span data-ttu-id="e328a-113">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="e328a-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
