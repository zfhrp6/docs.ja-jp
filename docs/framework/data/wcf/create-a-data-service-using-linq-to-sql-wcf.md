---
title: "方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, LINQ to SQL"
  - "WCF Data Services, プロバイダー"
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、エンティティ データはデータ サービスとして公開されます。  リフレクション プロバイダーでは、<xref:System.Linq.IQueryable%601> 実装を返すメンバーを公開するクラスに基づいたデータ モデルを定義できます。  データ ソース内のデータに更新を加えるには、これらのクラスも <xref:System.Data.Services.IUpdatable> インターフェイスを実装する必要があります。  詳細については、「[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)」を参照してください。  このトピックでは、リフレクション プロバイダーを使用して Northwind サンプル データベースにアクセスする LINQ to SQL クラスを作成する方法と、これらのデータ クラスに基づくデータ サービスを作成する方法について説明します。  
  
### LINQ to SQL クラスをプロジェクトに追加するには  
  
1.  Visual Basic または Visual C\# から、**\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[LINQ to SQL クラス\]** テンプレートをクリックします。  
  
3.  名前を「Northwind.dbml」に変更します。  
  
4.  **\[追加\]** をクリックします。  
  
     Northwind.dbml ファイルがプロジェクトに追加され、オブジェクト リレーショナル デザイナー \(O\/R デザイナー\) が開きます。  
  
5.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、Northwind の下にある **\[テーブル\]** を展開して、`Customers` テーブルをオブジェクト リレーショナル デザイナー \(O\/R デザイナー\) にドラッグします。  
  
     `Customer` エンティティ クラスが作成され、デザイン サーフェイスに表示されます。  
  
6.  `Orders` テーブル、`Order_Details` テーブル、および `Products` テーブルに対して手順 6 を繰り返します。  
  
7.  LINQ to SQL クラスを表す新しい .dbml ファイルを右クリックして、**\[コードの表示\]** をクリックします。  
  
     <xref:System.Data.Linq.DataContext> クラス \(この場合は `NorthwindDataContext`\) から継承するクラスの部分クラス定義を含む Northwind.cs という新しい分離コード ページが作成されます。  
  
8.  Northwind.cs コード ファイルの内容を次のコードに置き換えます。  このコードでは、<xref:System.Data.Linq.DataContext> と、および LINQ to SQL によって生成されたデータ クラスを拡張して、リフレクション プロバイダーを実装します。  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### LINQ to SQL ベースのデータ モデルを使用してデータ サービスを作成するには  
  
1.  **ソリューション エクスプローラー**で、ASP.NET プロジェクトの名前を右クリックし、**\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[WCF Data Service\]** をクリックします。  
  
3.  サービスの名前を入力して、**\[OK\]** をクリックします。  
  
     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。  既定では、コード エディターのウィンドウが開きます。  
  
4.  データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 \(この場合は `NorthwindDataContext`\) で置き換えます。  
  
5.  データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     指定した 3 つのエンティティ セットのリソースへのクライアント アクセスが承認されます。  
  
6.  Web ブラウザーを使用して Northwind.svc データ サービスをテストするには、トピック「[Web ブラウザーからサービスへのアクセス](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)」の手順に従います。  
  
## 参照  
 [方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)   
 [方法: リフレクション プロバイダーを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)   
 [データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)