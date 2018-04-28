---
title: WCF で使用されるセキュリティの概要
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: 15
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 72712e0934646a39c1e03a38716179384051003a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="security-concepts-used-in-wcf"></a>WCF で使用されるセキュリティの概要
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のセキュリティは、各種のセキュリティ インフラストラクチャで既に使用され展開されている概念の上に構築されています。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、これらのインフラストラクチャの一部 (SSL (Secure Sockets Layer) over HTTP (HTTPS) など) をサポートしています。 ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、新しい相互運用可能なセキュリティ標準 (WS-Security など) を SOAP エンコード メッセージに実装することで、既存のセキュリティ インフラストラクチャをサポートする以上の機能を実現しています。 既存の機構と新規の相互運用可能な標準のどちらを使用する場合でも、背後にあるセキュリティ概念に変わりはありません。 既存のインフラストラクチャおよび新しい標準を支える概念を理解することが、アプリケーションにとって最善のセキュリティ モデルを実装するための要になります。  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web サービスのセキュリティの概要  
 Microsoft Patterns and Practices グループは、ここからダウンロードされる WCF セキュリティ ガイダンスで、詳細なホワイト ペーパーを書き込みました。 [WCF セキュリティ ガイド](http://go.microsoft.com/fwlink/?LinkId=210210)です。 このホワイト ペーパーでは、Web サービス、WCF セキュリティの主な概念、イントラネット アプリケーション シナリオ、およびインターネット アプリケーション シナリオに関連するセキュリティの基本概念について説明しています。  
  
## <a name="industry-wide-security-specifications"></a>業界標準のセキュリティ仕様  
  
### <a name="public-key-infrastructure"></a>公開キー基盤  
 公開キー基盤 (PKI: Public Key Infrastructure) は、デジタル証明書、証明機関、およびその他の登録機関で構成されるシステムです。PKI では、公開キー暗号化を使用して、電子取引に関与する各当事者の検証と認証を行います。 詳細については、次を参照してください。 [Windows Server 2008 R2 の証明書サービス](http://go.microsoft.com/fwlink/?LinkId=210211)です。  
  
### <a name="kerberos-protocol"></a>Kerberos プロトコル  
 *Kerberos プロトコル*仕様は、Windows ドメインでユーザーを認証するためのセキュリティ機構を作成します。 ユーザーはドメイン内の他のエンティティと、セキュリティで保護されたコンテキストを確立できます。 Windows 2000 以降のプラットフォームでは、Kerberos プロトコルが既定で使用されます。 システムの機構を理解することは、イントラネット クライアントと対話するサービスを作成する場合に役立ちます。 さらに、以降、 *Web Services Security Kerberos Binding*広くが発行すると、ことができます、Kerberos プロトコルを使用するインターネット クライアントと通信 (つまり、Kerberos プロトコルは、相互運用可能な)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Kerberos プロトコルが Windows に実装されている方法を参照してください。 [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212)です。  
  
### <a name="x509-certificates"></a>X.509 証明書  
 X.509 証明書は、セキュリティ アプリケーションで使用される主要な資格情報の形式です。 詳細については、X.509 証明書を参照してください[X.509 公開キー証明書](http://go.microsoft.com/fwlink/?LinkId=210213)です。 X.509 証明書は証明書ストア内に格納されます。 Windows を実行しているコンピューターには、それぞれ目的が異なる数種類の証明書ストアがあります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 別のストアを参照してください[証明書ストア](http://go.microsoft.com/fwlink/?LinkID=87787)です。  
  
## <a name="web-services-security-specifications"></a>Web サービスのセキュリティ仕様  
 システム定義のバインディングでは、一般に使用されるさまざまな Web サービスのセキュリティ仕様をサポートしています。 システム指定のバインディングと、web サービス仕様の完全な一覧については、サポートを参照してください:[システム指定の相互運用性バインディングでサポートされる Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>アクセス制御機構  
 WCF には、サービスや操作へのアクセスを制御するさまざまな方法が用意されています。 次に例を示します。  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  ASP.NET メンバーシップ プロバイダー  
  
3.  ASP.NET ロール プロバイダー  
  
4.  承認マネージャー  
  
5.  ID モデル  
  
 詳細については、これらのトピックを参照してください、[アクセス制御機構](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>関連項目  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
