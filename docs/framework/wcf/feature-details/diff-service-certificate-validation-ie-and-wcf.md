---
title: "Internet Explorer と WCF で実行されるサービス証明書の検証の相違点"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a58ea9f84571ede9943769e1f187a242383a88f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer と WCF で実行されるサービス証明書の検証の相違点
HTTPS を使用した場合、Internet Explorer と [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ではサービス証明書の検証方法に違いがあるため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントからサービス エンドポイントに正常にメッセージを送信できても、サービスのヘルプ ページや Web サービス記述言語 (WSDL: Web Services Description Language) に Internet Explorer からアクセスできないことがあります。 これは、サービス証明書の拡張使用法フラグに `ServerAuthentication` オブジェクト識別子 (OID: Object Identifier) があるかどうかを Internet Explorer がチェックするのに対し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] はそのような制限を適用しないためです。 Internet Explorer がサービス ヘルプ ページまたはサービスの WSDL にアクセスできる場合を使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータにアクセスします。  
  
## <a name="see-also"></a>関連項目  
 [HTTPS、SSL over TCP、および SOAP セキュリティ間証明書検証の相違点](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [方法: メタデータを取得し、準拠サービスの実装](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
