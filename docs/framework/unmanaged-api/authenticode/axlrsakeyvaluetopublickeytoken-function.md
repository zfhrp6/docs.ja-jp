---
title: "_AxlRSAKeyValueToPublicKeyToken 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4af27a2abf1a0bcf4d79eda389c5f79f0ecb1eef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="09309-102">_AxlRSAKeyValueToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="09309-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="09309-103">Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。</span><span class="sxs-lookup"><span data-stu-id="09309-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09309-104">構文</span><span class="sxs-lookup"><span data-stu-id="09309-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09309-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09309-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="09309-106">[in]Base64 でエンコードされた Modulus blob (から、 \<Modulus > 要素)。</span><span class="sxs-lookup"><span data-stu-id="09309-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="09309-107">参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="09309-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="09309-108">[in]Base64 でエンコードされた Exponent blob (から、\<指数 > 要素)。</span><span class="sxs-lookup"><span data-stu-id="09309-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="09309-109">参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="09309-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="09309-110">[out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR * へのポインター。</span><span class="sxs-lookup"><span data-stu-id="09309-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09309-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="09309-111">Return Value</span></span>  
 <span data-ttu-id="09309-112">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="09309-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="09309-113">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="09309-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09309-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="09309-114">See Also</span></span>  
 [<span data-ttu-id="09309-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="09309-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
