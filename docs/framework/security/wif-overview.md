---
title: "Windows Identity Foundation 4.5 の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
caps.latest.revision: 11
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1e23b0261625efb1e6da070e4b5f8334b1ef7488
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="windows-identity-foundation-45-overview"></a>Windows Identity Foundation 4.5 の概要
Windows Identity Foundation 4.5 は、アプリケーション内でクレーム ベース ID を実装するための一連の .NET Framework クラスです。 このクラスを使用することで、クレーム対応アプリケーションおよびサービスのメリットを簡単に得られるようになります。 WIF 4.5 は、.NET Framework Version 4.5 以降が使用されているすべての Web アプリケーションまたは Web サービスで使用できます。 WIF は、オープン スタンダードに基づく業界共通の構想を取り入れた Microsoft のフェデレーション ID ソフトウェア ファミリの 1 つにすぎません。 フェデレーション ID は、[Active Directory® フェデレーション サービス](http://go.microsoft.com/fwlink/?LinkID=247516) (AD FS) 2.0、[Microsoft Azure のアクセス制御サービス](http://go.microsoft.com/fwlink/?LinkID=247517) (ACS)、および WIF の 3 つのコンポーネントで構成されます。 この 3 つのコンポーネントが一体となって、Microsoft の新しいクレーム ベースのクラウド ID およびアクセス プラットフォームのコアを形成しています。  
  
 WIF の詳細については、MSDN のセキュリティ デベロッパー センターの [Windows Identity Foundation の Web サイト](http://go.microsoft.com/fwlink/?LinkId=149009) (http://go.microsoft.com/fwlink/?LinkId=149009) を参照してください。 WIF を使用したアプリケーション作成の概要については、「[Windows Identity Foundation のプログラミング](http://go.microsoft.com/fwlink/?LinkId=210158)」(http://go.microsoft.com/fwlink/?LinkId=210158) (Vittorio Bertocci 著、Microsoft Press 発行) を参照してください。  
  
## <a name="wif-45-features"></a>WIF 4.5 の機能  
 WIF 4.5 は、ID 対応アプリケーションをビルドするためのフレームワークです。 このフレームワークは、WS-Trust プロトコルと WS-Federation プロトコルを抽象化し、クレーム対応アプリケーションと、必要に応じてセキュリティ トークン サービス (STS) をビルドするための API を開発者に提供します。 アプリケーションでは、WIF を使用して、AD FS 2.0、ACS などの STS から発行されたトークンを処理し、Web アプリケーションまたは Web サービスで ID ベースの決定を下すことができます。  
  
 WIF 4.5 の主な機能は次のとおりです。  
  
-   クレーム対応アプリケーション (証明書利用者アプリケーション) のビルド。 WIF は、開発者がクレーム対応アプリケーションをビルドするときに役立ちます。 WIF には、新しいクレーム モデルだけでなく豊富な API が用意されており、アプリケーション開発者は、この API を使用して、クレームに基づいてユーザー アクセスに関する決定を行うことができます。  また、アプリケーションを構築する環境として ASP.NET または WCF のどちらを選択した場合でも、WIF により一貫したプログラミングの操作性が実現します。  
  
-   クレーム対応アプリケーションに対する ID 委任のサポートの構築。  WIF には、複数のサービスの境界を越えて元の要求元の ID を保持する機能が用意されています。 この機能を有効にするには、フレームワークで "ActAs" 機能または "OnBehalfOf" 機能のいずれかを使用します。開発者は、この機能を使用して、ID 委任のサポートをクレーム対応アプリケーションに追加できます。  
  
-   カスタム STS のビルド。  WIF により、WS-Trust プロトコルをサポートするカスタム STS のビルドがかなり容易になりました。 この STS は、アクティブ STS とも呼ばれます。  
  
     また、フレームワークでは、WS-Federation をサポートする STS をビルドすることもでき、これにより Web ブラウザー クライアントが有効になります。 この STS は、パッシブ STS とも呼ばれます。  
  
-   新しい Identity and Access Tool for Visual Studio 11。このツールを使用すると、クレーム ベース ID を使用してアプリケーションを保護しながら、複数の ID プロバイダーからユーザーを受け入れることができます。 この WIF ツールは [http://go.microsoft.com/fwlink/?LinkID=245849](http://go.microsoft.com/fwlink/?LinkID=245849) からダウンロードできます。また、拡張機能マネージャーで直接 "ID" を検索して、Visual Studio 11 から直接ダウンロードすることもできます。 詳細については、「[Visual Studio 2012 の ID およびアクセス ツール](../../../docs/framework/security/identity-and-access-tool-for-vs.md)」を参照してください。  
  
 WIF がサポートする主なシナリオを次に示します。  
  
-   フェデレーション。  WIF では、複数のパートナー間のフェデレーションを有効にできます。 開発者はクレーム対応アプリケーション (RP) およびカスタム STS をビルドするための機能を使用して、このシナリオを実現します。  
  
-   ID の委任。  WIF ではサービスの境界を越えて ID を保持できるため、開発者は ID 委任のシナリオを簡単に実現できます。  
  
-   ステップアップ認証。 同じアプリケーション内でも、リソースによって認証の要件が異なる場合があります。 WIF では、認証要件を段階的に厳しくする必要がある (たとえば、最初はユーザー名とパスワード認証でログインし、その後、スマート カード認証にステップアップする) アプリケーションを、開発者がビルドできます。  
  
 WIF を使用すると、クレーム ベースの ID モデルのメリットを簡単に利用できます。 詳細については、[開発者向けの Windows Identity Foundation のホワイト ペーパー](http://go.microsoft.com/fwlink/?LinkId=122266)を参照してください。

