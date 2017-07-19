---
title: "WCF Data Services 4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Astoria"
  - "WCF Data Services, はじめに"
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# WCF Data Services 4.5
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] \(従来の "ADO.NET Data Services"\) は .NET Framework のコンポーネントです。このコンポーネントを使用すると、[Representational State Transfer \(REST\)](http://go.microsoft.com/fwlink/?LinkId=113919) のセマンティクスを使用して、Web またはイントラネット上のデータを公開および使用するために [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] を使用するサービスを作成できます。[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、URI でアドレス指定できるリソースとしてデータを公開します。  標準的な HTTP 動詞である GET、PUT、POST、および DELETE を使用してデータにアクセスし、変更できます。[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) のエンティティとリレーションシップの変換を使用して、アソシエーションによって関連付けられたエンティティのセットとしてリソースを公開します。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルを使用してリソースのアドレス指定および更新を行います。  このようにして、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] をサポートしている任意のクライアントからこれらのサービスにアクセスできます。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] を使用すると、XML としてデータを交換および更新するための標準のセットである Atom と、AJAX アプリケーションで広範に使用されるテキスト ベースのデータ交換形式である JavaScript Object Notation \(JSON\) という広く知られている転送形式を使用して、データをリソースに要求または書き込むことができます。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、さまざまなソースからのデータを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして公開できます。  Visual Studio のツールを使用すると、ADO.NET Entity Framework データ モデルを使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスを簡単に作成できます。[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードは、共通言語ランタイム \(CLR\) クラスに基づいて作成できます。また、遅延バインディングまたは型指定されていないデータに基づいて作成することもできます。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、クライアント ライブラリのセット \(一般的な .NET Framework クライアント アプリケーション用と Silverlight ベースのアプリケーション用\) も含まれています。  これらのクライアント ライブラリは、.NET Framework や Silverlight などの環境から [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスするときにオブジェクト ベースのプログラミング モデルを提供します。  
  
## 開始すべき場所  
 各自の興味に応じて、次のトピックのいずれかから [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の使用を開始することを検討してください。  
  
 すぐに使用を開始したい  
 -   [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [概要](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Silverlight のクイックスタート](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [Silverlight のクイックスタート \(Windows Phone 開発向け\)](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 コードを見たい  
 -   [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [方法: データ サービス クエリを実行する](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [方法: Windows Presentation Foundation 要素にデータをバインドする](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] について詳しく知りたい  
 -   [ホワイトペーパー: OData の導入](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Open Data Protocol Web サイト](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [OData: SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData: よくある質問](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 ビデオを見たい  
 -   [WCF Data Services ビギナーズ ガイド](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [WCF Data Services 開発者ビデオ](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [OData: 開発者 Web サイト](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 エンド ツー エンドのサンプルを見たい  
 -   [MSDN サンプル ギャラリーにある WCF Data Services ドキュメント サンプル](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [MSDN サンプル ギャラリーにあるその他の WCF Data Services ドキュメント サンプル](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [OData: SDK](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 Visual Studio との統合について知りたい  
 -   [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [Entity Framework プロバイダー](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 何に使用できるかを知りたい  
 -   [概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [ホワイトペーパー: OData の導入](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [アプリケーション シナリオ](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 Silverlight を使用したい  
 -   [Silverlight のクイックスタート](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [WCF Data Services \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Silverlight の概要](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 Windows Phone アプリケーションを作成したい  
 -   [Silverlight のクイックスタート \(Windows Phone 開発向け\)](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [Windows Phone 用 Open Data Protocol \(OData\) クライアント](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 LINQ を使用したい  
 -   [データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [LINQ に関する留意点](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [方法: データ サービス クエリを実行する](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 より詳しい情報が欲しい  
 -   [WCF Data Services チーム ブログ](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [リソース](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [WCF Data Services 開発者センター](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [Open Data Protocol Web サイト](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## このセクションの内容  
 [概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用可能な機能の概要について説明します。  
  
 [What's New in WCF Data Services](http://msdn.microsoft.com/ja-jp/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の新機能と、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の新機能のサポートについて説明します。  
  
 [概要](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開および使用する方法について説明します。  
  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開するデータ サービスを作成および構成する方法について説明します。  
  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 クライアント ライブラリを使用して .NET Framework クライアント アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する方法について説明します。  
  
## 参照  
 [Representational State Transfer \(REST\)](http://go.microsoft.com/fwlink/?LinkId=113919)