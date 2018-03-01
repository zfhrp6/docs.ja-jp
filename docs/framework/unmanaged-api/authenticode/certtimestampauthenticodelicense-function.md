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
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense 関数
Authenticode XrML ライセンスにタイム スタンプを付けます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSignedLicenseBlob`  
 [in] タイム スタンプが付けられる、署名付きの Authenticode XrML ライセンス。 参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。  
  
 `pwszTimestampURI`  
 [in] タイム スタンプ サーバーの URI。  
  
 `pTimestampSignatureBlob`  
 [out] base64 でエンコードされたタイム スタンプの署名を取得するための、CRYPT_DATA_BLOB へのポインター。 解放する、呼び出し元の責任である`pTimestampSignatureBlob` -> `pbData`で`HepFree()`使用後にします。 参照してください、 [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)構造体。  
  
## <a name="remarks"></a>コメント  
 タイム スタンプの署名は、実際は PKCS #7 SignedData メッセージで、この内容は、ライセンスの署名の SignatureValue のバイナリ形式です。 これは基本的に、ライセンスの副署名として機能します。  
  
## <a name="return-value"></a>戻り値  
 関数が成功した場合は `S_OK`。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
