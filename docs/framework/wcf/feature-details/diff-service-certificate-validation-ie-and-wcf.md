---
title: Internet Explorer と WCF で実行されるサービス証明書の検証の相違点
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: ecc2b16eae5428e305f5f6096d6d7994256d86c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488687"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer と WCF で実行されるサービス証明書の検証の相違点
Internet Explorer と Windows Communication Foundation (WCF) HTTP が使用されるときにサービス証明書の検証方法の違いにより、Internet Explorer はしないように、ヘルプ ページまたは Web サービス記述言語にアクセスできること(WSDL)、サービスの WCF クライアントが正常にできる場合でもメッセージ、サービス エンドポイントに送信します。 これは、Internet Explorer のチェックがあるため、サービス証明書があるかどうか、 `ServerAuthentication` WCF がこのような制約を適用していないはオブジェクト識別子 (OID) の拡張使用法フラグ。 Internet Explorer がサービス ヘルプ ページまたはサービスの WSDL にアクセスできる場合を使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータにアクセスします。  
  
## <a name="see-also"></a>関連項目  
 [HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [方法 : メタデータの取得および準拠サービスの実装をする](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
