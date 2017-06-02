---
title: "データ サービスの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# データ サービスの作成
このタスクでは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用するサンプル データ サービスを作成し、Northwind サンプル データベースに基づく [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードを公開します。この作業に必要な基本手順は次のとおりです。  
  
1.  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションを作成します。  
  
2.  [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ツールを使用して、データ モデルを定義します。  
  
3.  データ サービスを Web アプリケーションに追加します。  
  
4.  データ サービスへのアクセスを有効にします。  
  
> [!NOTE]
>  このタスクを完了するときに作成する [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションは、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で提供される [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発サーバー上で実行します。  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発サーバーは、ローカル コンピューターからのアクセスのみをサポートします。  開発時にデータ サービスのテストおよびトラブルシューティングを行いやすくするためにも、インターネット インフォメーション サービス \(IIS\) を使用して、データ サービスをホストするアプリケーションを実行することを検討してください。  詳細については、「[方法: IIS 上で実行する WCF Data Service を開発する](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。  
  
### ASP.NET Web アプリケーションを作成するには  
  
1.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] の下の **Web** テンプレートを選択し、**\[ASP.NET Web アプリケーション\]** をクリックします。  
  
    > [!NOTE]
    >  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer を使用する場合は、新しい Web アプリケーションではなく新しい Web サイトを作成する必要があります。  
  
3.  プロジェクトの名前として「`NorthwindService`」を入力します。  
  
4.  **\[OK\]** をクリックします。  
  
5.  \(省略可能\) Web アプリケーションに対して特定のポート番号を指定します。  メモ: このクイック スタートの以降の作業では、ポート番号 `12345` を使用します。  
  
    1.  **ソリューション エクスプローラー**で、作成した [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトの名前を右クリックし、**\[プロパティ\]** をクリックします。  
  
    2.  **\[Web\]** タブをクリックし、**\[ポートを指定する\]** ボックスの値を `12345` に設定します。  
  
### データ モデルを定義するには  
  
1.  **ソリューション エクスプローラー**で、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトの名前を右クリックし、**\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで **Data** テンプレートをクリックし、**\[ADO.NET エンティティ データ モデル\]** をクリックします。  
  
3.  データ モデルの名前として「`Northwind.edmx`」を入力します。  
  
4.  [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ウィザードで、**\[データベースから生成\]** をクリックし、**\[次へ\]** をクリックします。  
  
5.  次のいずれかの手順を実行し、データ モデルをデータベースに接続してから **\[次へ\]** をクリックします。  
  
    -   データベース接続がまだ構成されていない場合は、**\[新しい接続\]** をクリックして新しい接続を作成します。  詳細については、「[SQL Server データベースへの接続の作成方法](http://go.microsoft.com/fwlink/?LinkId=123631)」を参照してください。  この [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。  
  
         または  
  
    -   Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。  
  
6.  ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。  
  
7.  **\[完了\]** をクリックして、ウィザードを終了します。  
  
    > [!NOTE]
    >  この生成されたデータ モデルは、エンティティ型の外部キー プロパティを公開します。  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 を使用して作成したデータ モデルには、これらの外部キー プロパティが含まれません。  そのため、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 を使用して作成された Northwind データ サービスにアクセスしようとする前に、このバージョンの Northwind データ サービスにアクセスするために作成されたクライアント アプリケーションのクライアント データ サービス クラスを更新する必要があります。  
  
### データ サービスを作成するには  
  
1.  **ソリューション エクスプローラー**で、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトの名前を右クリックし、**\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[WCF Data Service\]** をクリックします。  
  
3.  サービスの名前として「`Northwind`」を入力します。  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。  既定では、コード エディターのウィンドウが開きます。  **ソリューション エクスプローラー**では、このサービスに Northwind という名前が付き、拡張子は .svc.cs または .svc.vb になります。  
  
4.  データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 \(この場合は `NorthwindEntities`\) で置き換えます。  クラス定義は次のようになります。  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### データ サービス リソースへのアクセスを有効にするには  
  
1.  データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     これにより、承認されたクライアントは、指定したエンティティ セットのリソースに読み取りおよび書き込みアクセスできるようになります。  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。  運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。  詳細については、「[WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。  
  
## 次の手順  
 ここでは、Northwind サンプル データベースに基づいて、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開する新しいデータ サービスを作成し、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションへのアクセス許可を持つクライアントからフィードへのアクセスを有効にしました。  次は、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] からデータ サービスを開始して、Web ブラウザーから HTTP GET 要求を送信して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスします。  
  
 [Web ブラウザーからサービスへのアクセス](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## 参照  
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ja-jp/91076853-0881-421b-837a-f582f36be527)