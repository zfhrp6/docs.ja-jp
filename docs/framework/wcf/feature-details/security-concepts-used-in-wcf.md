---
title: "WCF で使用されるセキュリティの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# WCF で使用されるセキュリティの概要
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のセキュリティは、各種のセキュリティ インフラストラクチャで既に使用され展開されている概念の上に構築されています。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、これらのインフラストラクチャの一部 \(SSL \(Secure Sockets Layer\) over HTTP \(HTTPS\) など\) をサポートしています。ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、新しい相互運用可能なセキュリティ標準 \(WS\-Security など\) を SOAP エンコード メッセージに実装することで、既存のセキュリティ インフラストラクチャをサポートする以上の機能を実現しています。既存の機構と新規の相互運用可能な標準のどちらを使用する場合でも、背後にあるセキュリティ概念に変わりはありません。既存のインフラストラクチャおよび新しい標準を支える概念を理解することが、アプリケーションにとって最善のセキュリティ モデルを実装するための要になります。  
  
## WCF Web サービスのセキュリティの概要  
 Microsoft Patterns and Practices グループでは、WCF セキュリティ ガイダンスに関する詳細なホワイト ペーパーを作成しました \(「[WCF セキュリティ ガイド](http://go.microsoft.com/fwlink/?LinkId=210210)」からダウンロードできます\)。このホワイト ペーパーでは、Web サービス、WCF セキュリティの主な概念、イントラネット アプリケーション シナリオ、およびインターネット アプリケーション シナリオに関連するセキュリティの基本概念について説明しています。  
  
## 業界標準のセキュリティ仕様  
  
### 公開キー基盤  
 公開キー基盤 \(PKI: Public Key Infrastructure\) は、デジタル証明書、証明機関、およびその他の登録機関で構成されるシステムです。PKI では、公開キー暗号化を使用して、電子取引に関与する各当事者の検証と認証を行います。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]、「[Windows Server 2008 R2 証明書サービス](http://go.microsoft.com/fwlink/?LinkId=210211)」を参照してください。  
  
### Kerberos プロトコル  
 *"Kerberos プロトコル"* は、Windows ドメインでユーザーを認証するセキュリティ機構を作成するための仕様です。ユーザーはドメイン内の他のエンティティと、セキュリティで保護されたコンテキストを確立できます。Windows 2000 以降のプラットフォームでは、Kerberos プロトコルが既定で使用されます。システムの機構を理解することは、イントラネット クライアントと対話するサービスを作成する場合に役立ちます。また、*Web Services Security Kerberos Binding* が広く公開されているため、Kerberos プロトコルを使用してインターネット クライアントと通信できます \(つまり、Kerberos プロトコルには相互運用性があります\)。Kerberos プロトコルを Windows で実装する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212)」を参照してください。  
  
### X.509 証明書  
 X.509 証明書は、セキュリティ アプリケーションで使用される主要な資格情報の形式です。X.509 証明書の詳細については、「[X.509 公開キー証明書](http://go.microsoft.com/fwlink/?LinkId=210213)」を参照してください。X.509 証明書は証明書ストア内に格納されます。Windows を実行しているコンピューターには、それぞれ目的が異なる数種類の証明書ストアがあります。各種ストア[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[証明書ストア](http://go.microsoft.com/fwlink/?LinkID=87787)」を参照してください。  
  
## Web サービスのセキュリティ仕様  
 システム定義のバインディングでは、一般に使用されるさまざまな Web サービスのセキュリティ仕様をサポートしています。システム定義のバインディングとサポートされる Web サービスの仕様の全一覧については、「[システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)」を参照してください。  
  
## アクセス制御機構  
 WCF には、サービスや操作へのアクセスを制御するさまざまな方法が用意されています。次に例を示します。  
  
1.  <xref:System.Security.Permissions.PrinciplePermissionAttribute>  
  
2.  ASP.NET メンバーシップ プロバイダー  
  
3.  ASP.NET ロール プロバイダー  
  
4.  承認マネージャー  
  
5.  ID モデル  
  
 各項目の詳細については、「[アクセス制御機構](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)」を参照してください。  
  
## 参照  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Windows Server AppFabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)