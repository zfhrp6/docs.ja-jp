---
title: "GetAppIdAuthority 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: GetAppIdAuthority
helpviewer_keywords: GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e89624feb04050534b917b865d5cb53b8c4cf58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getappidauthority-function"></a><span data-ttu-id="2ba28-102">GetAppIdAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="2ba28-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="2ba28-103">ポインターを取得、 [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)アプリケーション id と参照のキーを管理するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="2ba28-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ba28-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ba28-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ba28-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ba28-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="2ba28-106">[out]返された`IAppIdAuthority`ポインター。</span><span class="sxs-lookup"><span data-stu-id="2ba28-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ba28-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="2ba28-107">Requirements</span></span>  
 <span data-ttu-id="2ba28-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ba28-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ba28-109">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="2ba28-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="2ba28-110">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ba28-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba28-111">参照</span><span class="sxs-lookup"><span data-stu-id="2ba28-111">See Also</span></span>  
 [<span data-ttu-id="2ba28-112">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ba28-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 [<span data-ttu-id="2ba28-113">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="2ba28-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
