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
ms.openlocfilehash: f922cdba8bcfce6c9ff4543f6aea5bacfdc60ab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="72fd6-102">CertFreeAuthenticodeSignerInfo 関数</span><span class="sxs-lookup"><span data-stu-id="72fd6-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="72fd6-103">割り当てられたリソースを解放、 [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="72fd6-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72fd6-104">構文</span><span class="sxs-lookup"><span data-stu-id="72fd6-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72fd6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72fd6-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="72fd6-106">[in, out] リリースされる署名者情報。</span><span class="sxs-lookup"><span data-stu-id="72fd6-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="72fd6-107">参照してください、 [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="72fd6-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72fd6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="72fd6-108">Return Value</span></span>  
 <span data-ttu-id="72fd6-109">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="72fd6-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="72fd6-110">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="72fd6-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fd6-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="72fd6-111">See Also</span></span>  
 [<span data-ttu-id="72fd6-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="72fd6-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
