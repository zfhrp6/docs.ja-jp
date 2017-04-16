---
title: "方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, Entity Framework"
  - "WCF Data Services, プロバイダー"
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、エンティティ データはデータ サービスとして公開されます。  データ ソースがリレーショナル データベースの場合、このエンティティ データは [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] によって提供されます。  このトピックでは、既存のデータベースに基づき、このデータ モデルを使用して新しいデータ サービスを作成する [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web アプリケーションで [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] ベースのデータ モデルを作成する方法について説明します。  
  
 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] は、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] プロジェクトの外部に [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] モデルを生成できるコマンド ライン ツールも提供します。  詳細については、「[方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)」を参照してください。  
  
### 既存のデータベースに基づく Entity Framework モデルを既存の Web アプリケーションに追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[テンプレート\]** ペインの **\[データ\]** カテゴリをクリックして、**\[ADO.NET エンティティ データ モデル\]** をクリックします。  
  
3.  モデル名を入力して **\[追加\]** をクリックします。  
  
     [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ウィザードの最初のページが表示されます。  
  
4.  **\[モデルのコンテンツの選択\]** ダイアログ ボックスで **\[データベースから生成\]** をクリックします。  その後、**\[次へ\]** をクリックします。  
  
5.  **\[新しい接続\]** をクリックします。  
  
6.  **\[接続のプロパティ\]** ダイアログ ボックスでサーバー名を入力し、認証方法を選択します。データベース名を入力して **\[OK\]** をクリックします。  
  
     指定したデータベース接続の設定に従って **\[データ接続の選択\]** ダイアログ ボックスが更新されます。  
  
7.  **\[エンティティ接続設定に名前を付けて App.Config に保存\]** チェックボックスがオンになっていることを確認します。  その後、**\[次へ\]** をクリックします。  
  
8.  **\[データベース オブジェクトの選択\]** ダイアログ ボックスで、データ サービスで公開するすべてのデータベース オブジェクトを選択します。  
  
    > [!NOTE]
    >  データ モデルに含まれるオブジェクトは、データ サービスによって自動的には公開されません。  これらのオブジェクトは、サービス自身によって明示的に公開される必要があります。  詳細については、「[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)」を参照してください。  
  
9. **\[完了\]** をクリックしてウィザードを終了します。  
  
     特定のデータベースに基づく既定のデータ モデルが作成されます。  [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] では、データ モデルをカスタマイズできます。  詳細については、「[Tasks](http://msdn.microsoft.com/ja-jp/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb)」を参照してください。  
  
### 新しいデータ モデルを使用してデータ サービスを作成するには  
  
1.  データ モデルを表す .edmx ファイルを [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で開きます。  
  
2.  **モデル ブラウザー**でモデルを右クリックし、**\[プロパティ\]** をクリックしてエンティティ コンテナーの名前を確認します。  
  
3.  **ソリューション エクスプローラー**で、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトの名前を右クリックし、**\[新しい項目の追加\]** をクリックします。  
  
4.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[WCF Data Service\]** をクリックします。  
  
5.  サービスの名前を入力して、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で新しいサービスの XML マークアップおよびコード ファイルが作成されます。  既定では、コード エディターのウィンドウが開きます。  
  
6.  データ サービスのコードで、データ サービスを定義するクラスの定義内のコメント `/* TODO: put your data source class name here */` を <xref:System.Data.Objects.ObjectContext> クラスから継承する型で置き換えます。この型はデータ モデルのエンティティ コンテナー \(手順 2 で確認したコンテナー\) です。  
  
7.  データ サービスのコードで、承認されたクライアントがデータ サービスによって公開されているエンティティ セットにアクセスできるようにします。  詳細については、「[データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)」を参照してください。  
  
8.  Web ブラウザーを使用して Northwind.svc データ サービスをテストするには、トピック「[Web ブラウザーからサービスへのアクセス](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)」の手順に従います。  
  
## 参照  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)   
 [方法: リフレクション プロバイダーを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)   
 [方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)