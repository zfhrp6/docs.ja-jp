---
title: "方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 755df7c86d80214ded4e8c9534f88910a171c7a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、エンティティ データはデータ サービスとして公開されます。 リフレクション プロバイダーを使用すると、メンバーを公開する任意のクラスに基づいているデータ モデルの定義を返す、<xref:System.Linq.IQueryable%601>実装します。 データ ソース内のデータに更新を加えるには、これらのクラスも <xref:System.Data.Services.IUpdatable> インターフェイスを実装する必要があります。 詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)です。 このトピックでは、リフレクション プロバイダーを使用して Northwind サンプル データベースにアクセスする LINQ to SQL クラスを作成する方法と、これらのデータ クラスに基づくデータ サービスを作成する方法について説明します。  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a>LINQ to SQL クラスをプロジェクトに追加するには  
  
1.  Visual Basic または c# のアプリケーション内での**プロジェクト** メニューのをクリックして**新しい項目の追加**です。  
  
2.  クリックして、 **LINQ to SQL クラス**テンプレート。  
  
3.  名前を変更**Northwind.dbml**です。  
  
4.  **[追加]**をクリックします。  
  
     Northwind.dbml ファイルがプロジェクトに追加され、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開きます。  
  
5.  **サーバー**/**データベース エクスプ ローラー**、Northwind の下にある展開**テーブル**をドラッグし、`Customers`テーブルをオブジェクト リレーショナル デザイナー (O/Rデザイナーの場合)。  
  
     `Customer` エンティティ クラスが作成され、デザイン サーフェイスに表示されます。  
  
6.  `Orders` テーブル、`Order_Details` テーブル、および `Products` テーブルに対して手順 6 を繰り返します。  
  
7.  LINQ to SQL クラスとクリックを表す新しい .dbml ファイルを右クリックして**コードの表示**です。  
  
     <xref:System.Data.Linq.DataContext> クラス (この場合は `NorthwindDataContext`) から継承するクラスの部分クラス定義を含む Northwind.cs という新しい分離コード ページが作成されます。  
  
8.  Northwind.cs コード ファイルの内容を次のコードに置き換えます。 このコードでは、<xref:System.Data.Linq.DataContext> と、および LINQ to SQL によって生成されたデータ クラスを拡張して、リフレクション プロバイダーを実装します。  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>LINQ to SQL ベースのデータ モデルを使用してデータ サービスを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ASP.NET プロジェクトの名前を右クリックし、クリックして**新しい項目の追加**です。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**です。  
  
3.  サービスの名前を入力して、をクリックして**OK**です。  
  
     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。  
  
4.  データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindDataContext`) で置き換えます。  
  
5.  データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     指定した 3 つのエンティティ セットのリソースへのクライアント アクセスが承認されます。  
  
6.  Web ブラウザーを使用して Northwind.svc データ サービスをテストする、トピックの手順に従います[Web ブラウザーからサービスにアクセスする](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)です。  
  
## <a name="see-also"></a>参照  
 [方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [方法: リフレクション プロバイダーを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
