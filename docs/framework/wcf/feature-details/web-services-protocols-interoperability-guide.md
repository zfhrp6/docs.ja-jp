---
title: "Web サービス プロトコルの相互運用性ガイド | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# Web サービス プロトコルの相互運用性ガイド
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、さまざまな Web サービス プロトコルを実装します。  これらのプロトコルの多くには、さまざまなオプションと拡張ポイントが用意されており、それらの実装は実装者の裁量に任されています。  このトピックでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が実装する Web サービス プロトコルの一覧を示します。  サポートされる各プロトコルの実装の詳細については、このセクションの他のトピックで説明します。  
  
## WCF が実装する Web サービス プロトコル  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、チャネルを通じて Web サービス \(WS\) のインフラストラクチャ プロトコルをサポートし、コントラクト機能を通じて Web サービスのアプリケーション プロトコルをサポートします。  アプリケーション プロトコルの相互運用性は、XML スキーマ記述言語 \(XSD\) 1.0 と Web サービス記述言語 \(WSDL\) 1.1 を通じて実現されます。  
  
 インフラストラクチャ プロトコルの相互運用性は、WS\-\* 仕様によって提供されます。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネルには、さまざまな WS\-\* インフラストラクチャ プロトコルのサポートが用意されています。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネルは、バインド要素を使用して構成されます。  さまざまな [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインド要素によって実装される WS\-\* インフラストラクチャ プロトコルの完全な一覧を次の表に示します。  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> は、次の表の仕様をサポートします。  
  
|仕様\/ドキュメント|Link|  
|----------------|----------|  
|HTTP 1.1|[RFC 2616](http://go.microsoft.com/fwlink/?LinkId=90372)|  
|SOAP 1.1 HTTP バインディング|[簡易オブジェクト アクセス プロトコル \(SOAP\) 1.1](http://go.microsoft.com/fwlink/?LinkId=90520)、セクション 7|  
|SOAP 1.2 HTTP バインディング|[SOAP バージョン 1.2 第 2 部: Adjuncts \(第 2 版\)](http://go.microsoft.com/fwlink/?LinkId=95329)、セクション 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> および <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> は、次の表の仕様をサポートします。  
  
|仕様\/ドキュメント|Link|  
|----------------|----------|  
|XML|[拡張マークアップ言語 \(XML\) 1.0 \(第 4 版\)](http://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1.1|[簡易オブジェクト アクセス プロトコル \(SOAP\) 1.1](http://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 コア|[SOAP バージョン 1.2 第 1 部: Messaging Framework \(第 2 版\)](http://go.microsoft.com/fwlink/?LinkId=94664)|  
|WS\-Addressing 2004\/08|[Web Services Addressing \(WS\-Addressing\)](http://go.microsoft.com/fwlink/?LinkId=81239)|  
|W3C Web Services Addressing 1.0 \- コア|[Web Services Addressing 1.0 \- コア](http://go.microsoft.com/fwlink/?LinkId=96688)|  
|W3C Web Services Addressing 1.0 \- SOAP バインディング|[Web Services Addressing 1.0 \- SOAP バインディング](http://go.microsoft.com/fwlink/?LinkId=96689)|  
|W3C Web Services Addressing 1.0 \- WSDL バインディング\*|[Web Services Addressing 1.0 \- WSDL バインディング](http://go.microsoft.com/fwlink/?LinkId=96690)|  
|W3C Web Services Addressing 1.0 \- メタデータ|[Web Services Addressing 1.0 \- メタデータ](http://www.w3.org/TR/ws-addr-metadata/)|  
|WSDL SOAP1.1 バインディング|[Web サービス記述言語 \(WSDL\) 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)|  
|WSDL SOAP1.2 バインディング|[WSDL 1.1 Binding Extension for SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> は、次の表の仕様をサポートします。  
  
|仕様\/ドキュメント|Link|  
|----------------|----------|  
|XOP|[XML\-binary Optimized Packaging](http://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM \+ SOAP1.2 バインディング|[SOAP Message Transmission Optimization Mechanism](http://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM SOAP 1.1 バインディング|[SOAP 1.1 Binding for MTOM 1.0](http://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS\-Policy アサーション|未公開|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> は、次の表の仕様をサポートします。  
  
|仕様\/ドキュメント|Link|  
|----------------|----------|  
|WSS SOAP Message Security 1.0|[Web Services Security: SOAP Message Security 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS: Username Token Profile 1.0|[Web Services Security UsernameToken Profile 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> Password\/@Type\=PasswordText \(既定\) が必要です。|  
|WSS: X.509 Token Profile 1.0|[Web Services Security X.509 Certificate Token Profile](http://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS: SAML 1.1 Token Profile 1.0|[Web Services Security: SAML Token Profile](http://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS SOAP Message Security 1.1|[Web Services Security: SOAP Message Security 1.1](http://go.microsoft.com/fwlink/?LinkId=91240)|  
|WSS Username Token Profile 1.1|[Web Services Security UsernameToken Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> パスワード ベースのキー派生は実装していません。<br /><br /> Password\/@Type\=PasswordText \(既定\) が必要です。|  
|WSS: X509 Token Profile 1.1|[Web Services Security X.509 Certificate Token Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: Kerberos Token Profile 1.1|[Web Services Security Kerberos Token Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS: SAML 1.1 Token Profile 1.1|[Web Services Security SAML Token Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS\-SecureConversation|[Web Services Secure Conversation Language](http://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS\-Trust 1.4|[Web Services Trust Language](http://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS\-SecurityPolicy 2005\/07|[Web Services Secure Conversation Language](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> OASIS WS\-SX 技術委員会に提出された正誤表で修正されています。<br /><br /> [ws\-sx message](http://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS\-ReliableMessaging 1.1|[リライアブル メッセージング プロトコル バージョン 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> は、次の表の仕様をサポートします。  
  
|仕様\/ドキュメント|Link|  
|----------------|----------|  
|WS\-Coordination|[Web Services Coordination](http://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS\-AtomicTransaction|[Web Services Atomic Transaction](http://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 <xref:System.ServiceModel.Description.MetadataExporter>、<xref:System.ServiceModel.Description.MetadataImporter>、<xref:System.ServiceModel.Description.WSDLExporter>、<xref:System.ServiceModel.Description.WSDLImporter>、および <xref:System.ServiceModel.Description.MetadataResolver> の各クラスは、次のメタデータ仕様をサポートします。  
  
-   [XML スキーマ第 1 部: 構造第 2 版](http://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [XML スキーマ第 2 部: データ型第 2 版](http://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS\-Policy 1.2](http://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS\-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS\-PolicyAttachment 1.2](http://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS\-MetadataExchange 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [WS\-Transfer メタデータ取得のための Get](http://go.microsoft.com/fwlink/?LinkId=96708)  
  
 さらに、次の相互運用性プロファイルが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 間で実装されます。  
  
-   [Basic Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Simple SOAP Binding 1.0](http://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Basic Security Profile 1.0 草案](http://go.microsoft.com/fwlink/?LinkId=96711)  
  
## 参照  
 [システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)   
 [メッセージング プロトコル](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)   
 [データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)   
 [WSDL とポリシー](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)   
 [セキュリティ プロトコル](../../../../docs/framework/wcf/feature-details/security-protocols.md)   
 [信頼できるメッセージング プロトコル バージョン 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)   
 [リライアブル メッセージング プロトコル バージョン 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)   
 [トランザクション プロトコル](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)   
 [コンテキスト交換プロトコル](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)