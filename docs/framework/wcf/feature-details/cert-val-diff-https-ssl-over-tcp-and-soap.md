---
title: "HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "証明書 [WCF], 検証方法の相違点"
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、HTTP \(HTTPS\) または TCP を介したトランスポート層セキュリティ \(TLS\) だけでなく、メッセージ層 \(SOAP\) セキュリティでも証明書を使用できます。ここでは、このような証明書の検証方法の違いについて説明します。  
  
## HTTPS クライアント証明書の検証  
 HTTPS を使用してクライアントとサービス間で通信を行う場合、サービスに対して認証を行うためにクライアントが使用する証明書はチェーン信頼をサポートしている必要があります。つまり、信頼されたルート証明機関にチェーンされている必要があります。チェーンされていない場合は、HTTP レイヤーで <xref:System.Net.WebException> が発生し、メッセージ "リモート サーバーがエラーを返しました: \(403\) 使用不可能" が表示されます。この例外は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって <xref:System.ServiceModel.Security.MessageSecurityException> として示されます。  
  
## HTTP サービス証明書の検証  
 HTTPS を使用してクライアントとサービス間で通信を行う場合、サーバーが認証に使用する証明書は既定でチェーン信頼をサポートしている必要があります。つまり、信頼されたルート証明機関にチェーンされている必要があります。証明書が失効しているかどうかを確認するためのオンライン チェックは行われません。この動作は、<xref:System.Net.Security.RemoteCertificateValidationCallback> コールバックを登録することによってオーバーライドできます。コードは次のようになります。  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 <!-- TODO: review snippet reference [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  -->  
  
 `ValidateServerCertificate` の署名は次のようになります。  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 `ValidateServerCertificate` を実装すると、サービス証明書を検証するために必要であるとクライアント アプリケーションの開発者が考える、すべてのチェックを実行できます。  
  
## SSL over TCP または SOAP セキュリティにおけるクライアント証明書の検証  
 SSL \(Secure Sockets Layer\) over TCP またはメッセージ \(SOAP\) セキュリティを使用する場合、クライアント証明書は <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> クラスの <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> プロパティ値に従って検証されます。プロパティは <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値のいずれかに設定されます。失効チェックは <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> クラスの <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> プロパティの値に応じて実行されます。プロパティは <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値のいずれかに設定されます。  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## SSL over TCP および SOAP セキュリティにおけるサービス証明書の検証  
 SSL over TCP またはメッセージ \(SOAP\) セキュリティを使用する場合、サービス証明書は <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> クラスの <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> プロパティ値に従って検証されます。プロパティは <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値のいずれかに設定されます。  
  
 失効チェックは <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> クラスの <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> プロパティの値に応じて実行されます。プロパティは <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値のいずれかに設定されます。  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## 参照  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>   
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)