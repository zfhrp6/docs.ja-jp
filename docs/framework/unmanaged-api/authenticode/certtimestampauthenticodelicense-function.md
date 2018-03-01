---
title: "CertTimestampAuthenticodeLicense 関数"
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
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53241a459f561bdfd8fc5cb077cb8384f1d906b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="126aa-102">CertTimestampAuthenticodeLicense 関数</span><span class="sxs-lookup"><span data-stu-id="126aa-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="126aa-103">Authenticode XrML ライセンスにタイム スタンプを付けます。</span><span class="sxs-lookup"><span data-stu-id="126aa-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="126aa-104">構文</span><span class="sxs-lookup"><span data-stu-id="126aa-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="126aa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="126aa-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="126aa-106">[in] タイム スタンプが付けられる、署名付きの Authenticode XrML ライセンス。</span><span class="sxs-lookup"><span data-stu-id="126aa-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="126aa-107">参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="126aa-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="126aa-108">[in] タイム スタンプ サーバーの URI。</span><span class="sxs-lookup"><span data-stu-id="126aa-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="126aa-109">[out] base64 でエンコードされたタイム スタンプの署名を取得するための、CRYPT_DATA_BLOB へのポインター。</span><span class="sxs-lookup"><span data-stu-id="126aa-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="126aa-110">解放する、呼び出し元の責任である`pTimestampSignatureBlob` -> `pbData`で`HepFree()`使用後にします。</span><span class="sxs-lookup"><span data-stu-id="126aa-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="126aa-111">参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="126aa-111">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="126aa-112">コメント</span><span class="sxs-lookup"><span data-stu-id="126aa-112">Remarks</span></span>  
 <span data-ttu-id="126aa-113">タイム スタンプの署名は、実際は PKCS #7 SignedData メッセージで、この内容は、ライセンスの署名の SignatureValue のバイナリ形式です。</span><span class="sxs-lookup"><span data-stu-id="126aa-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="126aa-114">これは基本的に、ライセンスの副署名として機能します。</span><span class="sxs-lookup"><span data-stu-id="126aa-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="126aa-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="126aa-115">Return Value</span></span>  
 <span data-ttu-id="126aa-116">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="126aa-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="126aa-117">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="126aa-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126aa-118">参照</span><span class="sxs-lookup"><span data-stu-id="126aa-118">See Also</span></span>  
 [<span data-ttu-id="126aa-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="126aa-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
