---
title: WCF Data Services 4.5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- HTML
- VB
- CSharp
- C++
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1b491d644112137cb24e847439aa133691e5261d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] (従来の "ADO.NET Data Services") は .NET Framework のコンポーネントです。このコンポーネントを使用すると、[Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) のセマンティクスを使用し、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] を使用して Web またはイントラネット上のデータを公開および使用するサービスを作成できます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、URI でアドレス指定できるリソースとしてデータを公開します。 標準的な HTTP 動詞である GET、PUT、POST、および DELETE を使用してデータにアクセスし、変更できます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) のエンティティとリレーションシップの規則を使用して、アソシエーションによって関連付けられたエンティティのセットとしてリソースを公開します。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルを使用してリソースのアドレス指定および更新を行います。 このようにして、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] をサポートしている任意のクライアントからこれらのサービスにアクセスできます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] を使用すると、XML としてデータを交換および更新するための標準のセットである Atom と、AJAX アプリケーションで広範に使用されるテキスト ベースのデータ交換形式である JavaScript Object Notation (JSON) という広く知られている転送形式を使用して、データをリソースに要求または書き込むことができます。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、さまざまなソースからのデータを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして公開できます。 Visual Studio のツールを使用すると、ADO.NET Entity Framework データ モデルを使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスを簡単に作成できます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードは、共通言語ランタイム (CLR) クラスに基づいて作成できます。また、遅延バインディング データまたは型指定されていないデータに基づいて作成することもできます。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、クライアント ライブラリのセット (一般的な .NET Framework クライアント アプリケーション用と Silverlight ベースのアプリケーション用) も含まれています。 これらのクライアント ライブラリは、.NET Framework や Silverlight などの環境から [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスするときにオブジェクト ベースのプログラミング モデルを提供します。  
  
## <a name="where-should-i-start"></a>開始すべき場所  
 各自の興味に応じて、次のトピックのいずれかから [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の使用を開始することを検討してください。  
  
 すぐに使用を開始したい  
 -   [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Silverlight クイックスタート](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [Windows Phone 開発用の Silverlight クイック スタート](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 コードを見たい  
 -   [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [方法: データ サービス クエリを実行する](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [方法: Windows Presentation Foundation 要素にデータをバインドする](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] について詳しく知りたい  
 -   [ホワイト ペーパー: OData の概要](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Open Data Protocol Web サイト](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [OData: SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData: よく寄せられる質問](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 ビデオを見たい  
 -   [WCF Data Services のビギナーズ ガイド](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [WCF Data Services 開発者用ビデオ](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [OData: 開発者 Web サイト](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 エンド ツー エンドのサンプルを見たい  
 -   [MSDN サンプル ギャラリーの WCF Data Services ドキュメントのサンプル](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [MSDN サンプル ギャラリーのその他の WCF Data Services サンプル](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [OData: SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 Visual Studio との統合について知りたい  
 -   [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [Entity Framework プロバイダー](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 何に使用できるかを知りたい  
 -   [概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [ホワイト ペーパー: OData の概要](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [アプリケーション シナリオ](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 Silverlight を使用したい  
 -   [Silverlight クイックスタート](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Silverlight について](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 Windows Phone アプリケーションを作成したい  
 -   [Windows Phone 開発用の Silverlight クイック スタート](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [Windows Phone の Open Data Protocol (OData) クライアント](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 LINQ を使用したい  
 -   [データ サービスに対するクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [LINQ に関する留意点](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [方法: データ サービス クエリを実行する](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 より詳しい情報が欲しい  
 -   [WCF Data Services チームのブログ](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [リソース](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [WCF Data Services デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [Open Data Protocol Web サイト](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用可能な機能の概要について説明します。  
  
 [WCF Data Services の新機能](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の新機能と、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の新機能のサポートについて説明します。  
  
 [はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開および使用する方法について説明します。  
  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開するデータ サービスを作成および構成する方法について説明します。  
  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 クライアント ライブラリを使用して .NET Framework クライアント アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)

