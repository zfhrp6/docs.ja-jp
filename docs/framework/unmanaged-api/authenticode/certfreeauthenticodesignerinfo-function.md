---
title: "CertFreeAuthenticodeSignerInfo 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeSignerInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8b38d30a1323d0d44330b8bb9a006c372ea7780
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="fb959-102">CertFreeAuthenticodeSignerInfo 関数</span><span class="sxs-lookup"><span data-stu-id="fb959-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="fb959-103">割り当てられたリソースを解放、 [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="fb959-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb959-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb959-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb959-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb959-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="fb959-106">[in, out] リリースされる署名者情報。</span><span class="sxs-lookup"><span data-stu-id="fb959-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="fb959-107">参照してください、 [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="fb959-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb959-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="fb959-108">Return Value</span></span>  
 <span data-ttu-id="fb959-109">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="fb959-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="fb959-110">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="fb959-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb959-111">参照</span><span class="sxs-lookup"><span data-stu-id="fb959-111">See Also</span></span>  
 [<span data-ttu-id="fb959-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="fb959-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
