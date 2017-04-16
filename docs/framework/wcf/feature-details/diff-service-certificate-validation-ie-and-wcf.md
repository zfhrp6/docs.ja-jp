---
title: "Internet Explorer と WCF で実行されるサービス証明書の検証の相違点 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "証明書 [WCF], サービス証明書の検証"
  - "サービス証明書の検証 [WCF]"
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Internet Explorer と WCF で実行されるサービス証明書の検証の相違点
HTTPS を使用した場合、Internet Explorer と [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ではサービス証明書の検証方法に違いがあるため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントからサービス エンドポイントに正常にメッセージを送信できても、サービスのヘルプ ページや Web サービス記述言語 \(WSDL: Web Services Description Language\) に Internet Explorer からアクセスできないことがあります。これは、サービス証明書の拡張使用法フラグに `ServerAuthentication` オブジェクト識別子 \(OID: Object Identifier\) があるかどうかを Internet Explorer がチェックするのに対し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] はそのような制限を適用しないためです。サービスのヘルプ ページまたはサービスの WSDL に Internet Explorer からアクセスできないときは、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用してそのサービスのメタデータにアクセスします。  
  
## 参照  
 [HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)   
 [方法 : メタデータの取得および準拠サービスの実装をする](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)