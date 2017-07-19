---
title: "初めてのクレーム対応 WCF サービスのビルド | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# 初めてのクレーム対応 WCF サービスのビルド
## 対象  
  
-   Windows Identity Foundation \(WIF\)  
  
-   Windows Communication Foundation \(WCF\)  
  
## 概要  
 このトピックでは、WIF を使用してクレーム対応 WCF サービスをビルドするシナリオの概要について説明します。  クレーム対応 Web サービスのシナリオには、通常、Web サービス、エンド ユーザー、セキュリティ トークン サービス \(STS\) の 3 つ参加要素が存在します。  次の図は、このシナリオについて説明しています。  
  
 ![WIF 基本要求に対応する WCF サービス](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.png "WIFBasicClaimsAwareWCFService")  
  
1.  WCF サービス クライアント \(エージェントと呼ばれることもあります\) は、WIF を使用して資格情報を STS に送信します。認証が正常に行われると、STS はそのエージェントに対してトークンを発行します。  
  
2.  エージェントは、この STS によって発行されたトークンを WCF サービスに送信します。  
  
3.  クレーム対応 WCF サービスは、STS とその STS が発行したトークンを信頼するように構成され、  WIF を使用してトークンを検証し、解析します。  開発者は、承認の実装などのアプリケーションのニーズに応じて、適切な WIF API と種類 \(**ClaimsPrincipal** など\) を使用します。  
  
 .NET 4.5 以降、WIF は .NET Framework パッケージに含まれています。  .NET Framework 自体で直接 WIF クラスを使用できるため、.NET プラットフォームでクレーム ベースの ID をより深く統合し、クレームをさらに簡単に使用できます。  WIF 4.5 を使用すると、クレーム対応アプリケーションの開発を開始する目的で、帯域外コンポーネントをインストールする必要がありません。  WIF クラスは、さまざまなアセンブリに分散されています。主なものは、System.Security.Claims、System.IdentityModel、および System.IdentityModel.Services です。  
  
 STS は、認証が正常に行われたときにトークンを発行するサービスです。  Microsoft では、2 つの業界標準 STS を提供します。  
  
-   [Active Directory フェデレーション サービス \(AD FS\) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=247516\)  
  
-   [Windows Azure Access Control Service \(ACS\)](http://go.microsoft.com/fwlink/?LinkID=247517) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=247517\).  
  
 AD FS 2.0 は、Windows Server R2 に含まれており、設置型シナリオの STS として使用できます。  Azure Active Directory アクセス制御 \(Access Control Service または ACS とも呼ばれます\) は、Microsoft Azure の一部として提供されるクラウド サービスです。  テストまたは学習の目的で、他の STS を使用して、クレーム対応アプリケーションをビルドすることもできます。  たとえば、オンラインで自由に入手できる [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=245849\) に含まれる、ローカル開発用 STS を使用できます。  
  
 WIF を使用して初めてのクレーム対応 WCF サービスをビルドするには、「[How To: Build Claims\-Aware WCF Service Using WIF](http://msdn.microsoft.com/ja-jp/431e6415-62ed-4a9f-af03-f14d2b4dfe6d)」を参照してください。  
  
## 参照  
 [WIF の概要](../../../docs/framework/security/getting-started-with-wif.md)