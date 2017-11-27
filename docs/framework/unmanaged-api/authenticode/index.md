---
title: "Authenticode (アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e90a13ebf46f1891061c78435b7ba47d68de001d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (アンマネージ API リファレンス)
Authenticode XrML ライセンスの作成および検証モジュールをサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [_AxlGetIssuerPublicKeyHash 関数](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。  
  
 [_AxlPublicKeyBlobToPublicKeyToken 関数](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。  
  
 [_AxlRSAKeyValueToPublicKeyToken 関数](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。  
  
 [CertFreeAuthenticodeSignerInfo 関数](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 AXL_AUTHENTICODE_SIGNER_INFO 構造に割り当てられているリソースを解放します。  
  
 [CertFreeAuthenticodeTimestamperInfo 関数](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造に割り当てられているリソースを開放します。  
  
 [CertTimestampAuthenticodeLicense 関数](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 CertCreateAuthenticodeLicense で作成された Authenticode XrML ライセンスにタイム スタンプを付けます。  
  
 [CertVerifyAuthenticodeLicense 関数](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 Authenticode XrML ライセンスの有効性を検証します。  
  
 [AXL_AUTHENTICODE_SIGNER_INFO 構造体](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 Authenticode の署名者情報を定義します。  
  
 [AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造体](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 Authenticode のタイム スタンパー情報を定義します。  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ API リファレンス](../../../../docs/framework/unmanaged-api/index.md)
