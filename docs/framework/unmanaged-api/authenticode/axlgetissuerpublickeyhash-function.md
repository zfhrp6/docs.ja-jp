---
title: "_AxlGetIssuerPublicKeyHash 関数"
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
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fee2b3e0e74ec13009a9b02d226c6a99b0e2f34b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="ae935-102">_AxlGetIssuerPublicKeyHash 関数</span><span class="sxs-lookup"><span data-stu-id="ae935-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="ae935-103">指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="ae935-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae935-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae935-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae935-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae935-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="ae935-106">[in] CSP 公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="ae935-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="ae935-107">参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="ae935-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="ae935-108">[out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR \* へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ae935-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae935-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ae935-109">Return Value</span></span>  
 <span data-ttu-id="ae935-110">関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="ae935-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae935-111">参照</span><span class="sxs-lookup"><span data-stu-id="ae935-111">See Also</span></span>  
 [<span data-ttu-id="ae935-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ae935-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
