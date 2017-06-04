---
title: "方法: IIS 上で実行する WCF Data Service を開発する | Microsoft Docs"
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
  - "WCF Data Services, 配置"
  - "WCF Data Services, 開発"
  - "WCF Data Services, ホスティング"
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 方法: IIS 上で実行する WCF Data Service を開発する
このトピックでは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用して、Northwind サンプル データベースに基づいてデータ サービスを作成する方法を示します。このサンプル データベースは、インターネット インフォメーション サービス \(IIS\) 上で動作する ASP.NET Web アプリケーションによってホストされます。  同じ Northwind データ サービスを ASP.NET 開発サーバーで実行する ASP.NET Web アプリケーションとして作成する方法については、「[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)」を参照してください。  
  
> [!NOTE]
>  Northwind データ サービスを作成するには、ローカル コンピューターに Northwind サンプル データベースをインストールしておく必要があります。  このサンプル データベースをダウンロードするには、ダウンロード ページ「[SQL Server のサンプル データベース](http://go.microsoft.com/fwlink/?linkid=24758)」を参照してください。  
  
 このトピックでは、Entity Framework プロバイダーを使用してデータ サービスを作成する方法を示します。  その他のデータ サービス プロバイダーを利用することもできます。  詳細については、「[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)」を参照してください。  
  
 サービスを作成した後に、データ サービス リソースへのアクセスを明示的に提供する必要があります。  詳細については、「[方法: データ サービスへのアクセスを有効にする](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)」を参照してください。  
  
### IIS 上で実行する ASP.NET Web アプリケーションを作成するには  
  
1.  Visual Studio の **\[ファイル\]** メニューで、**\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、プログラム言語として \[Visual Basic\] または \[Visual C\#\] のいずれかを選択します。  
  
3.  **\[テンプレート\]** ペインで、**\[ASP.NET Web アプリケーション\]** を選択します。  メモ : Visual Studio Web Developer を使用する場合は、新しい Web アプリケーションではなく、新しい Web サイトを作成する必要があります。  
  
4.  プロジェクトの名前として「`NorthwindService`」を入力します。  
  
5.  **\[OK\]** をクリックします。  
  
6.  **\[プロジェクト\]** メニューで **\[NorthwindService のプロパティ\]** を選択します。  
  
7.  **\[Web\]** タブで **\[ローカル IIS Web サーバーを使用する\]** を選択します。  
  
8.  **\[仮想ディレクトリの作成\]**、**\[OK\]** の順にクリックします。  
  
9. 管理特権を持つコマンド プロンプトから、次のコマンドを実行します \(オペレーティング システムによって異なります\)。  
  
    -   32 ビット システム:  
  
        ```ms-dos  
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   64 ビット システム:  
  
        ```ms-dos  
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     これにより、コンピューターに Windows Communication Foundation \(WCF\) が登録されます。  
  
10. 管理特権を持つコマンド プロンプトから、次のコマンドを実行します \(オペレーティング システムによって異なります\)。  
  
    -   32 ビット システム:  
  
        ```ms-dos  
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   64 ビット システム:  
  
        ```ms-dos  
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     これにより、WCF がコンピューターにインストールされた後、IIS は正常に実行されます。  IIS の再起動が必要になる場合があります。  
  
11. ASP.NET アプリケーションが IIS7 で実行されると、次の手順も実行する必要があります。  
  
    1.  IIS マネージャーを開いて **\[既定の Web サイト\]** の下にある PhotoService アプリケーションに移動します。  
  
    2.  **\[機能ビュー\]** で、**\[認証\]** をダブルクリックします。  
  
    3.  **\[認証\]** ページで、**\[匿名認証\]** をクリックします。  
  
    4.  **\[操作\]** ペインで **\[編集\]** をクリックして、匿名ユーザーがサイトに接続するセキュリティ プリンシパルを設定します。  
  
    5.  **\[匿名認証資格情報の編集\]** ダイアログ ボックスで、**\[アプリケーション プール ID\]** をクリックします。  
  
    > [!IMPORTANT]
    >  ネットワーク サービス アカウントを使用する際、そのアカウントに関連するすべての内部ネットワーク アクセス権を匿名ユーザーに付与します。  
  
12. SQL Server Management Studio、sqlcmd.exe ユーティリティ、または Visual Studio の Transact\-SQL エディターを使用して、Northwind データベースがアタッチされた SQL Server のインスタンスに対して次の Transact\-SQL コマンドを実行します。  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     これにより、IIS の実行に使用される Windows アカウントに対して、SQL Server インスタンスのログインが作成されます。  IIS は、これを使用して SQL Server インスタンスに接続できるようになります。  
  
13. Northwind データベースをアタッチして、次の Transact\-SQL コマンドを実行します。  
  
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
  
### データ モデルを定義するには  
  
1.  **ソリューション エクスプローラー**で、ASP.NET プロジェクトの名前を右クリックし、**\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで **\[ADO.NET エンティティ データ モデル\]** を選択します。  
  
3.  データ モデルの名前として「`Northwind.edmx`」を入力します。  
  
4.  エンティティ データ モデル ウィザードで、**\[データベースから生成\]** を選択し、**\[次へ\]** をクリックします。  
  
5.  次のいずれかの手順を実行し、データ モデルをデータベースに接続してから **\[次へ\]** をクリックします。  
  
    -   データベース接続がまだ構成されていない場合は、**\[新しい接続\]** をクリックして新しい接続を作成します。  詳細については、「[SQL Server データベースへの接続の作成方法](http://go.microsoft.com/fwlink/?LinkId=123631)」を参照してください。  この [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。  
  
         または  
  
    -   Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。  
  
6.  ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。  
  
7.  **\[完了\]** をクリックして、ウィザードを終了します。  
  
    > [!NOTE]
    >  この生成されたデータ モデルは、エンティティ型の外部キー プロパティを公開します。  Visual Studio 2008 を使用して作成したデータ モデルには、これらの外部キー プロパティが含まれません。  そのため、Visual Studio 2008 を使用して作成された Northwind データ サービスにアクセスしようとする前に、このバージョンの Northwind データ サービスにアクセスするために作成されたクライアント アプリケーションのクライアント データ サービス クラスを更新する必要があります。  
  
### データ サービスを作成するには  
  
1.  **ソリューション エクスプローラー**で、ASP.NET プロジェクトの名前を右クリックし、**\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[ADO.NET Data Service\]** を選択します。  
  
3.  サービスの名前として「`Northwind`」を入力します。  
  
     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。  既定では、コード エディターのウィンドウが開きます。  **ソリューション エクスプローラー**では、このサービスに Northwind という名前が付き、拡張子は .svc.cs または .svc.vb になります。  
  
4.  データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 \(この場合は `NorthwindEntities`\) で置き換えます。  クラス定義は次のようになります。  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## 参照  
 [サービスとしてのデータの公開](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)