---
title: "方法: IIS 上で実行する WCF Data Service を開発する"
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
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b93b6e8b6e687f2e39fd5792aba08eaa47fa29fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>方法: IIS 上で実行する WCF Data Service を開発する
このトピックは、使用する方法を示します[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]でインターネット インフォメーション サービス (IIS) を実行している ASP.NET Web アプリケーションによってホストされる Northwind サンプル データベースに基づくデータ サービスを作成します。 ASP.NET 開発サーバーで実行されている ASP.NET Web アプリケーションとして同じ Northwind データ サービスを作成する方法の例は、次を参照してください。、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。  
  
> [!NOTE]
>  Northwind データ サービスを作成するには、ローカル コンピューターに Northwind サンプル データベースをインストールしておく必要があります。 このサンプル データベースをダウンロードするには、ダウンロード ページ「 [SQL Server 用サンプル データベース](http://go.microsoft.com/fwlink/?linkid=24758)」を参照してください。  
  
 このトピックでは、Entity Framework プロバイダーを使用してデータ サービスを作成する方法を示します。 その他のデータ サービス プロバイダーを利用することもできます。 詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)です。  
  
 サービスを作成した後に、データ サービス リソースへのアクセスを明示的に提供する必要があります。 詳細については、次を参照してください。[する方法: データ サービスへのアクセスの有効化](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)です。  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a>IIS 上で実行する ASP.NET Web アプリケーションを作成するには  
  
1.  Visual Studio での**ファイル**メニューの **新規**、し、**プロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、プログラミング言語と Visual Basic または Visual c# のいずれかを選択します。  
  
3.  **テンプレート**ペインで、 **ASP.NET Web アプリケーション**です。 メモ : Visual Studio Web Developer を使用する場合は、新しい Web アプリケーションではなく、新しい Web サイトを作成する必要があります。  
  
4.  型`NorthwindService`として、プロジェクトの名前。  
  
5.  **[OK]**をクリックします。  
  
6.  **プロジェクト**メニューの  **NorthwindService プロパティ**です。  
  
7.  選択、 **Web** 、タブをクリックし**ローカル IIS Web サーバー**です。  
  
8.  をクリックして**仮想ディレクトリの作成** をクリックし、 **OK**です。  
  
9. 管理特権を持つコマンド プロンプトから、次のコマンドを実行します (オペレーティング システムによって異なります)。  
  
    -   32 ビット システム:   
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   64 ビット システム:   
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     これにより、コンピューターに Windows Communication Foundation (WCF) が登録されます。  
  
10. 管理特権を持つコマンド プロンプトから、次のコマンドを実行します (オペレーティング システムによって異なります)。  
  
    -   32 ビット システム:   
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   64 ビット システム:   
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     これにより、WCF がコンピューターにインストールされた後、IIS は正常に実行されます。 IIS の再起動が必要になる場合があります。  
  
11. ASP.NET アプリケーションが IIS7 で実行されると、次の手順も実行する必要があります。  
  
    1.  IIS マネージャーを開きの下にある PhotoService アプリケーションに移動**Default Web Site**です。  
  
    2.  **機能ビュー**をダブルクリックして**認証**です。  
  
    3.  **認証**] ページで、[**匿名認証**です。  
  
    4.  **アクション** ウィンドウで、をクリックして**編集**を設定するセキュリティ プリンシパルを匿名ユーザーの下、サイトに接続します。  
  
    5.  **匿名認証資格情報の編集**ダイアログ ボックスで、**アプリケーション プール id**です。  
  
    > [!IMPORTANT]
    >  ネットワーク サービス アカウントを使用する際、そのアカウントに関連するすべての内部ネットワーク アクセス権を匿名ユーザーに付与します。  
  
12. SQL Server Management Studio、sqlcmd.exe ユーティリティ、または Visual Studio の Transact-SQL エディターを使用して、Northwind データベースがアタッチされた SQL Server のインスタンスに対して次の Transact-SQL コマンドを実行します。  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     これにより、IIS の実行に使用される Windows アカウントに対して、SQL Server インスタンスのログインが作成されます。 IIS は、これを使用して SQL Server インスタンスに接続できるようになります。  
  
13. Northwind データベースをアタッチして、次の Transact-SQL コマンドを実行します。  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     これにより、新しいログインに権限が付与され、IIS は Northwind データベースに対してデータの読み取りおよび書き込みを行うことができるようになります。  
  
### <a name="to-define-the-data-model"></a>データ モデルを定義するには  
  
1.  **ソリューション エクスプ ローラー**を ASP.NET プロジェクトの名前を右クリックし、をクリックして**新しい項目の追加。**  
  
2.  **新しい項目の追加**ダイアログ ボックスで、 **ADO.NET エンティティ データ モデル**です。  
  
3.  データ モデルの名前を入力`Northwind.edmx`です。  
  
4.  エンティティ データ モデル ウィザードで、次のように選択します。**データベースから生成**、クリックして**次**です。  
  
5.  次の手順のいずれかの手順を実行して、データ モデルをデータベースに接続し、をクリックして**次**:  
  
    -   データベース接続が既に構成されていない場合にクリックして**新しい接続**し、新しい接続を作成します。 詳細については、次を参照してください。[する方法: SQL Server データベースへの接続の作成](http://go.microsoft.com/fwlink/?LinkId=123631)です。 この [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。  
  
         \- または  
  
    -   Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。  
  
6.  ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。  
  
7.  をクリックして**完了**ウィザードを閉じます。  
  
    > [!NOTE]
    >  この生成されたデータ モデルは、エンティティ型の外部キー プロパティを公開します。 Visual Studio 2008 を使用して作成したデータ モデルには、これらの外部キー プロパティが含まれません。 そのため、Visual Studio 2008 を使用して作成された Northwind データ サービスにアクセスしようとする前に、このバージョンの Northwind データ サービスにアクセスするために作成されたクライアント アプリケーションのクライアント データ サービス クラスを更新する必要があります。  
  
### <a name="to-create-the-data-service"></a>データ サービスを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ASP.NET プロジェクトの名前を右クリックし、クリックして**新しい項目の追加**です。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、 **ADO.NET データ サービス**です。  
  
3.  サービスの名前を入力`Northwind`です。  
  
     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。 **ソリューション エクスプ ローラー**サービスの名前は、Northwind、拡張子を持つ。 svc.cs または.svc.vb になります。  
  
4.  データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindEntities`) で置き換えます。 クラス定義は次のようになります。  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a>参照  
 [サービスとしてのデータの公開](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
