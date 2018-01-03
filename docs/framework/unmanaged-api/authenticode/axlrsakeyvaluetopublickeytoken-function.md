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
ms.workload: dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="663b6-102">_AxlRSAKeyValueToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="663b6-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="663b6-103">Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。</span><span class="sxs-lookup"><span data-stu-id="663b6-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="663b6-104">構文</span><span class="sxs-lookup"><span data-stu-id="663b6-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="663b6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="663b6-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="663b6-106">[in]Base64 でエンコードされた Modulus blob (から、 \<Modulus > 要素)。</span><span class="sxs-lookup"><span data-stu-id="663b6-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="663b6-107">参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="663b6-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="663b6-108">[in]Base64 でエンコードされた Exponent blob (から、\<指数 > 要素)。</span><span class="sxs-lookup"><span data-stu-id="663b6-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="663b6-109">参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="663b6-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="663b6-110">[out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR * へのポインター。</span><span class="sxs-lookup"><span data-stu-id="663b6-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="663b6-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="663b6-111">Return Value</span></span>  
 <span data-ttu-id="663b6-112">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="663b6-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="663b6-113">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="663b6-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="663b6-114">参照</span><span class="sxs-lookup"><span data-stu-id="663b6-114">See Also</span></span>  
 [<span data-ttu-id="663b6-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="663b6-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
