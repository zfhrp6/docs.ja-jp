---
title: "クレーム対応の ASP.NET Web アプリケーションを初めて構築する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# クレーム対応の ASP.NET Web アプリケーションを初めて構築する
## 対象  
  
-   Windows Identity Foundation \(WIF\)  
  
-   ASP.NET  
  
 このトピックでは、WIF を使用してクレーム対応 ASP.NET Web アプリケーションをビルドするシナリオの概要について説明します。  クレーム対応アプリケーションのシナリオには、通常、アプリケーション、エンド ユーザー、セキュリティ トークン サービス \(STS\) の 3 つ参加要素が存在します。  次の図は、このシナリオについて説明しています。  
  
 ![WIF 基本 Web アプリ](../../../docs/framework/security/media/wifbasicwebapp.png "WIFBasicWebApp")  
  
1.  クレーム対応アプリケーションは、認証されていない要求を WIF で特定し、その要求を STS にリダイレクトします。  
  
2.  エンド ユーザーは資格情報を STS に提供します。認証が正常に行われると、STS はそのユーザーに対してトークンを発行します。  
  
3.  ユーザーは、要求内の STS 発行のトークンと共に、STS からクレーム対応アプリケーションにリダイレクトされます。  
  
4.  クレーム対応アプリケーションは、STS とその STS が発行したトークンを信頼するように構成され、  WIF を使用してトークンを検証し、解析します。  開発者は、承認の実装などのアプリケーションのニーズに応じて、適切な WIF API と種類 \(**ClaimsPrincpal** など\) を使用します。  
  
 .NET 4.5 以降、WIF は .NET Framework パッケージに含まれています。  .NET Framework 自体で直接 WIF クラスを使用できるため、.NET プラットフォームでクレーム ベースの ID をより深く統合し、クレームをさらに簡単に使用できます。  WIF 4.5 を使用すると、クレーム対応アプリケーションの開発を開始する目的で、帯域外コンポーネントをインストールする必要がありません。  WIF クラスは、さまざまなアセンブリに分散されています。主なものは、System.Security.Claims、System.IdentityModel、および System.IdentityModel.Services です。  
  
 STS は、認証が正常に行われたときにトークンを発行するサービスです。  Microsoft では、2 つの業界標準 STS を提供します。  
  
-   [Active Directory フェデレーション サービス \(AD FS\) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=247516\)  
  
-   [Microsoft Azure のアクセス制御サービス \(ACS\)](http://go.microsoft.com/fwlink/?LinkID=247517) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=247517\)。  
  
 AD FS 2.0 は、Windows Server R2 に含まれており、設置型シナリオの STS として使用できます。  ACS は、Microsoft Azure プラットフォームの一部として提供されるクラウド サービスです。  テストまたは学習の目的で、他の STS を使用して、クレーム対応アプリケーションをビルドすることもできます。  たとえば、オンラインで自由に入手できる [Identity and Access Tool for Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkID=245849) \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=245849\) に含まれる、ローカル開発用 STS を使用できます。  
  
 WIF を使用してクレーム対応 ASP.NET アプリケーションを初めてビルドするには、次のいずれかの手順に従ってください。  
  
-   [方法: WIF を使用してクレーム対応 ASP.NET MVC Web アプリケーションをビルドする](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [方法: フォームベースの認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## 参照  
 [WIF の概要](../../../docs/framework/security/getting-started-with-wif.md)