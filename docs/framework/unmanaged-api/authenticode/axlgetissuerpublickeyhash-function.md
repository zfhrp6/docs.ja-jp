---
title: _AxlGetIssuerPublicKeyHash 関数
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b197aa539e60a9dbcee55cf190c44b45da3a5fb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402016"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="789fd-102">_AxlGetIssuerPublicKeyHash 関数</span><span class="sxs-lookup"><span data-stu-id="789fd-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="789fd-103">指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="789fd-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="789fd-104">構文</span><span class="sxs-lookup"><span data-stu-id="789fd-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="789fd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="789fd-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="789fd-106">[in] CSP 公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="789fd-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="789fd-107">参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="789fd-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="789fd-108">[out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR \* へのポインター。</span><span class="sxs-lookup"><span data-stu-id="789fd-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="789fd-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="789fd-109">Return Value</span></span>  
 <span data-ttu-id="789fd-110">関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="789fd-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789fd-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="789fd-111">See Also</span></span>  
 [<span data-ttu-id="789fd-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="789fd-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
