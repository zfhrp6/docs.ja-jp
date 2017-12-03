---
title: "方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77a4b90b16a92e993d9283932b2a609f874c7568
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、エンティティ データはデータ サービスとして公開されます。 データ ソースがリレーショナル データベースの場合、このエンティティ データは [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] によって提供されます。 このトピックでは、既存のデータベースに基づき、このデータ モデルを使用して新しいデータ サービスを作成する [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Web アプリケーションで [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] ベースのデータ モデルを作成する方法について説明します。  
  
 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] は、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロジェクトの外部に [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] モデルを生成できるコマンド ライン ツールも提供します。 詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルの生成に使用する EdmGen.exe](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)です。  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>既存のデータベースに基づく Entity Framework モデルを既存の Web アプリケーションに追加するには  
  
1.  **プロジェクト** メニューのをクリックして**新しい項目の追加**です。  
  
2.  **テンプレート** ウィンドウで、をクリックして、**データ**カテゴリ、および選択**ADO.NET エンティティ データ モデル**です。  
  
3.  モデルの名前を入力し、クリックして**追加**です。  
  
     [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ウィザードの最初のページが表示されます。  
  
4.  **モデルのコンテンツ**ダイアログ ボックスで、**データベースから生成**です。 その後、 **[次へ]**をクリックします。  
  
5.  クリックして、**新しい接続**ボタンをクリックします。  
  
6.  **接続プロパティ**ダイアログ ボックスで、サーバー名を入力、認証方法を選択して、データベース名を入力および順にクリックして**OK**です。  
  
     **データ接続の選択**データベース接続の設定 ダイアログ ボックスを更新します。  
  
7.  いることを確認、**エンティティ接続設定を付けて App.Config に保存します。**チェック ボックスをオンします。 その後、 **[次へ]**をクリックします。  
  
8.  **データベース オブジェクトの選択**ダイアログ ボックスで、すべてのデータベースのオブジェクトがデータ サービスの公開を計画することです。  
  
    > [!NOTE]
    >  データ モデルに含まれるオブジェクトは、データ サービスによって自動的には公開されません。 これらのオブジェクトは、サービス自身によって明示的に公開される必要があります。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)です。  
  
9. をクリックして**完了**ウィザードを完了します。  
  
     特定のデータベースに基づく既定のデータ モデルが作成されます。 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] では、データ モデルをカスタマイズできます。 詳細については、[タスク](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb)に関する記事を参照してください。  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a>新しいデータ モデルを使用してデータ サービスを作成するには  
  
1.  データ モデルを表す .edmx ファイルを [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で開きます。  
  
2.  **モデル ブラウザー**モデルを右クリックしをクリックして**プロパティ**、エンティティ コンテナーの名前をメモします。  
  
3.  **ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトをクリックして**新しい項目の追加**です。  
  
4.  **新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**です。  
  
5.  サービスの名前を入力して、をクリックして**OK**です。  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。  
  
6.  データ サービスのコードで、データ サービスを定義するクラスの定義内のコメント `/* TODO: put your data source class name here */` を <xref:System.Data.Objects.ObjectContext> クラスから継承する型で置き換えます。この型はデータ モデルのエンティティ コンテナー (手順 2 で確認したコンテナー) です。  
  
7.  データ サービスのコードで、承認されたクライアントがデータ サービスによって公開されているエンティティ セットにアクセスできるようにします。 詳細については、次を参照してください。[データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)です。  
  
8.  Web ブラウザーを使用して Northwind.svc データ サービスをテストする、トピックの手順に従います[Web ブラウザーからサービスにアクセスする](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [方法: リフレクション プロバイダーを使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [方法: SQL データ ソースを LINQ を使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
