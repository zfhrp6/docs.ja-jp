---
title: データ サービスの作成
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 781def411214b0804cdc094c00b2f655b6c3823d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="creating-the-data-service"></a>データ サービスの作成
このタスクを使用するサンプル データ サービスを作成する[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]を公開する、 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Northwind サンプル データベースに基づいているフィード。 このタスクに必要な基本手順は次のとおりです。  
  
1.  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションを作成します。  
  
2.  [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ツールを使用して、データ モデルを定義します。  
  
3.  データ サービスを Web アプリケーションに追加します。  
  
4.  データ サービスへのアクセスを有効にします。  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]でこのタスクを完了するときに作成する Web アプリケーションを実行、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Visual Studio によって提供される開発サーバーです。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発サーバーは、ローカル コンピューターからのアクセスのみをサポートします。 開発時にデータ サービスのテストおよびトラブルシューティングを行いやすくするためにも、インターネット インフォメーション サービス (IIS) を使用して、データ サービスをホストするアプリケーションを実行することを検討してください。 詳細については、「 [方法: IIS 上で実行する WCF Data Service を開発する](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。  
  
### <a name="to-create-the-aspnet-web-application"></a>ASP.NET Web アプリケーションを作成するには  
  
1.  Visual Studio での**ファイル**メニューの **新規**、し、**プロジェクト**です。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、Visual Basic または Visual c# のいずれかを選択して、 **Web**テンプレート、および選択**ASP.NET Web アプリケーション**です。  
  
    > [!NOTE]
    >  Visual Studio Web Developer を使用する場合は、新しい Web アプリケーションではなく新しい Web サイトを作成する必要があります。  
  
3.  型`NorthwindService`として、プロジェクトの名前。  
  
4.  **[OK]** をクリックします。  
  
5.  (省略可能) Web アプリケーションに対して特定のポート番号を指定します。 メモ: このクイック スタートの以降の作業では、ポート番号 `12345` を使用します。  
  
    1.  **ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトだけが作成されると、クリックして**プロパティ**です。  
  
    2.  選択、 **Web**タブをクリックしの値を設定、**特定のポート**テキスト ボックスに`12345`です。  
  
### <a name="to-define-the-data-model"></a>データ モデルを定義するには  
  
1.  **ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトをクリックして**新しい項目の追加。**  
  
2.  **新しい項目の追加**ダイアログ ボックスで、をクリックして、**データ**クリックしてテンプレート**ADO.NET エンティティ データ モデル**です。  
  
3.  データ モデルの名前を入力`Northwind.edmx`です。  
  
4.  [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]ウィザードで、**データベースから生成**、順にクリック**次**です。  
  
5.  次の手順のいずれかの手順を実行して、データ モデルをデータベースに接続し、をクリックして**次**:  
  
    -   データベース接続が既に構成されていない場合にクリックして**新しい接続**し、新しい接続を作成します。 詳細については、次を参照してください。[する方法: SQL Server データベースへの接続の作成](http://go.microsoft.com/fwlink/?LinkId=123631)です。 この SQL Server インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。  
  
         \- または -  
  
    -   Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。  
  
6.  ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。  
  
7.  をクリックして**完了**ウィザードを閉じます。  
  
    > [!NOTE]
    >  この生成されたデータ モデルは、エンティティ型の外部キー プロパティを公開します。 Visual Studio 2008 を使用して作成したデータ モデルには、これらの外部キー プロパティが含まれません。 そのため、Visual Studio 2008 を使用して作成された Northwind データ サービスにアクセスしようとする前に、このバージョンの Northwind データ サービスにアクセスするために作成されたクライアント アプリケーションのクライアント データ サービス クラスを更新する必要があります。  
  
### <a name="to-create-the-data-service"></a>データ サービスを作成するには  
  
1.  **ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトをクリックして**新しい項目の追加**です。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**です。  
  
3.  サービスの名前を入力`Northwind`です。  
  
     StudioVisual の visual Studio では、新しいサービスの XML マークアップおよびコード ファイルを作成します。 既定では、コード エディターのウィンドウが開きます。 **ソリューション エクスプ ローラー**サービスの名前は、Northwind、拡張子を持つ。 svc.cs または.svc.vb になります。  
  
4.  データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindEntities`) で置き換えます。 クラス定義は次のようになります。  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a>データ サービス リソースへのアクセスを有効にするには  
  
1.  データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     これにより、承認されたクライアントは、指定したエンティティ セットのリソースに読み取りおよび書き込みアクセスできるようになります。  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。 運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。 詳細については、「 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。  
  
## <a name="next-steps"></a>次の手順  
 公開する新しいデータ サービスが正常に作成、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]に対する権限があるクライアントからフィードへのアクセスを有効にして、Northwind サンプル データベースに基づいてフィード、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションです。 次は、Visual Studio からデータ サービスを開始して、Web ブラウザーから HTTP GET 要求を送信して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスします。  
  
 [Web ブラウザーからサービスへのアクセス](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
