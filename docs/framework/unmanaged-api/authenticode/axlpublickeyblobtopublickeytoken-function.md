---
title: "_AxlPublicKeyBlobToPublicKeyToken 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlPublicKeyBlobToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25a6a78fad95b894e82a75159458f25264f0ee0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="ed2ad-102">_AxlPublicKeyBlobToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="ed2ad-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="ed2ad-103">CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。</span><span class="sxs-lookup"><span data-stu-id="ed2ad-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed2ad-104">構文</span><span class="sxs-lookup"><span data-stu-id="ed2ad-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed2ad-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed2ad-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="ed2ad-106">[in] CSP 公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="ed2ad-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="ed2ad-107">[out] 16 進エンコードされた公開キー ハッシュを受け取るための WCHAR * へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed2ad-107">[out] A pointer to WCHAR * to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed2ad-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ed2ad-108">Return Value</span></span>  
 <span data-ttu-id="ed2ad-109">関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="ed2ad-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed2ad-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed2ad-110">See Also</span></span>  
 [<span data-ttu-id="ed2ad-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ed2ad-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
