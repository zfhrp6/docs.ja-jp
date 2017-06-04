---
title: "データ サービスのホスティング (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 構成"
  - "WCF Data Services, Windows Communication Foundation"
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# データ サービスのホスティング (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用して、データを [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードとして公開するサービスを作成できます。  このデータ サービスは、<xref:System.Data.Services.DataService%601> から継承されたクラスとして定義されます。  このクラスは、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] からの要求に応じて、要求メッセージの処理、データ ソースに対する更新の実行、および応答メッセージの生成に必要な機能を提供します。ただし、データ サービスは、受信 HTTP 要求のネットワーク ソケットにバインドしたり、これをリッスンしたりすることはできません。  この機能要件のため、データ サービスはホスティング コンポーネントに依存します。  
  
 データ サービス ホストは、データ サービスに代わって次のタスクを実行します。  
  
-   要求をリッスンし、その要求をデータ サービスにルーティングする。  
  
-   要求ごとにデータ サービスのインスタンスを作成する。  
  
-   受信要求を処理するようデータ サービスに要求する。  
  
-   データ サービスに代わって応答を送信する。  
  
 データ サービスのホスティングを簡素化するため、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は Windows Communication Foundation \(WCF\) と統合するように設計されています。  データ サービスは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションでデータ サービス ホストとして機能する既定の WCF 実装を提供します。  そのため、次のいずれかの方法でデータ サービスをホストできます。  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーション  
  
-   自己ホスト型 WCF サービスをサポートするマネージ アプリケーション  
  
-   その他のカスタム データ サービス ホスト  
  
## ASP.NET アプリケーションでのデータ サービスのホスト  
 Visual Studio の **\[新しい項目の追加\]** ダイアログを使用して ASP.NET アプリケーションにデータ サービスを定義すると、プロジェクトに 2 つの新しいファイルが生成されます。  そのうち一方のファイル \(拡張子は `.svc`\) は、データ サービスのインスタンス化方法を WCF ランタイムに指示します。  たとえば、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成される Northwind サンプル データ サービスの .svc ファイルは次のようになります。  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 このディレクティブは、<xref:System.Data.Services.DataServiceHostFactory> クラスを使用して、名前付きのデータ サービス クラスのサービス ホストを作成するようアプリケーションに指示します。  
  
 `.svc` ファイルの分離コード ページには、データ サービス自体の実装であるクラスが含まれます。Northwind サンプル データ サービスの場合、このクラスは次のように定義されます。  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 データ サービスは WCF サービスと同様に動作するため、データ サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] と統合され、WCF Web プログラミング モデルに従います。詳細については、「[WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)」と「[WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)」を参照してください。  
  
## 自己ホスト型 WCF サービス  
 WCF 実装が組み込まれている [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、WCF サービスとして自己ホスト型のデータ サービスをサポートします。  サービスは、コンソール アプリケーションなどの任意の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションで自己ホスト型とすることができます。  <xref:System.ServiceModel.Web.WebServiceHost> を継承する <xref:System.Data.Services.DataServiceHost> クラスを使用して、特定のアドレスでデータ サービスをインスタンス化します。  
  
 自己ホストを使用するとサービスの配置とトラブルシューティングが容易になるので、開発時やテスト時に役立ちます。  ただし、この種類のホスティングでは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] またはインターネット インフォメーション サービス \(IIS\) に備わっている高度なホスト機能や管理機能を使用できません。詳細については、「[マネージ アプリケーションのホスト](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)」を参照してください。  
  
## カスタム データ サービス ホストの定義  
 WCF ホストの実装の制限が厳格すぎる場合、データ サービスのカスタム ホストを定義することもできます。  <xref:System.Data.Services.IDataServiceHost> インターフェイスを実装する任意のクラスをデータ サービスのネットワーク ホストとして使用できます。  カスタム ホストは、<xref:System.Data.Services.IDataServiceHost> インターフェイスを実装し、データ サービス ホストの次の基本的な役割を果たすことができるようにする必要があります。  
  
-   データ サービスにサービス ルート パスを提供する。  
  
-   適切な <xref:System.Data.Services.IDataServiceHost> メンバーの実装に対する要求ヘッダーおよび応答ヘッダーの情報を処理する。  
  
-   データ サービスで発生する例外を処理する。  
  
-   クエリ文字列のパラメーターを検証する。  
  
## 参照  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [サービスとしてのデータの公開](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)   
 [データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)