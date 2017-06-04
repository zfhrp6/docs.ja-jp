---
title: "WCF Data Services の開発と配置 | Microsoft Docs"
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
  - "WCF Data Services, 開発"
  - "WCF Data Services, 配置"
  - "配置 [WCF Data Services]"
  - "アプリケーションの開発 [WCF Data Services]"
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# WCF Data Services の開発と配置
このトピックでは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の開発と配置について説明します。[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の他の基本情報については、「[概要](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)」および「[概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)」を参照してください。  
  
## WCF Data Services の開発  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用して、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] をサポートするデータ サービスを作成する場合、開発時に次の基本的なタスクを実行する必要があります。  
  
1.  **データ モデルを定義する**  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、リレーショナル データベースから遅延バインディング データ型に至るさまざまなデータ ソースのデータに基づいてデータ モデルを定義できるようにする各種のデータ サービス プロバイダーをサポートしています。 詳細については、「[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)」を参照してください。  
  
2.  **データ サービスを作成する**  
  
     最も基本的なデータ サービスでは、<xref:System.Data.Services.DataService%601> クラスを継承するクラスを `T` 型 \(エンティティ コンテナーの名前空間修飾名\) と一緒に公開します。 詳細については、「[WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)」を参照してください。  
  
3.  **データ サービスを構成する**  
  
     既定では、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、エンティティ コンテナーによって公開されているリソースへのアクセスは無効になります。<xref:System.Data.Services.DataServiceConfiguration> インターフェイスを使用すると、リソースとサービス操作へのアクセスの構成、サポートされる [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] のバージョンの指定、およびサービス全体のその他の動作 \(バッチ動作や 1 つの応答フィードで返すことができるエンティティの最大数など\) を定義できます。 詳細については、「[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックでは、主に、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を使用したデータ サービスの開発と配置について説明します。 データを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして公開できるようにする [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の柔軟性については、「[WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)」を参照してください。  
  
### 開発 Web サーバーの選択  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を使用して WCF Data Services を [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションまたは [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web サイトとして開発する場合、開発時にデータ サービスを実行する Web サーバーを選択できます。 次の Web サーバーを [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] と統合することにより、ローカル コンピューターでデータ サービスを簡単にテストおよびデバッグできるようになります。  
  
1.  **ローカル IIS サーバー**  
  
     インターネット インフォメーション サービス \(IIS\) で実行される [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションまたは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サイトとしてデータ サービスを作成する場合は、ローカル コンピューターで IIS を使用してデータ サービスを開発およびテストすることをお勧めします。 IIS でデータ サービスを実行すると、デバッグ時における HTTP 要求のトレースが容易になります。 また、データ サービスに必要なファイルやデータベースなどのリソースにアクセスするために IIS で必要とされる権限を事前に確認することもできます。 IIS でデータ サービスを実行するには、IIS と [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] がインストールされて正しく構成されており、ファイル システムおよびデータベースで IIS アカウントにアクセス権が付与されている必要があります。 詳細については、「[方法: IIS 上で実行する WCF Data Service を開発する](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。  
  
    > [!NOTE]
    >  開発環境でローカル IIS サーバーを構成できるようにするには、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を管理者権限で実行する必要があります。  
  
2.  **Visual Studio 開発サーバー**  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] には、組み込みの Web サーバーとして、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] プロジェクトの既定の Web サーバーである [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発サーバーが用意されています。 この Web サーバーは、開発時にローカル コンピューターで [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトを実行するように設計されています。 「[WCF Data Services クイックスタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)」では、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 開発サーバーで実行されるデータ サービスを作成する方法を示しています。  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 開発サーバーを使用してデータ サービスを開発する場合は、次の制限事項に注意する必要があります。  
  
    -   このサーバーにはローカル コンピューター上でしかアクセスできません。  
  
    -   このサーバーは、HTTP メッセージの既定のポートであるポート 80 ではなく、`localhost` および特定のポートでリッスンします。 詳細については、「[ASP.NET Web プロジェクト用の Visual Studio の Web サーバー](http://msdn.microsoft.com/ja-jp/31d4f588-df59-4b7e-b9ea-e1f2dd204328)」を参照してください。  
  
    -   このサーバーでは、現在のユーザー アカウントのコンテキストでデータ サービスが実行されます。 たとえば、管理者レベルのユーザーとして実行する場合、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 開発サーバーで実行されるデータ サービスは、管理者レベルの特権を持ちます。 そのため、データ サービスは、IIS サーバーに配置されたときにはアクセスする権限を持たないリソースにも、アクセスできることになります。  
  
    -   このサーバーには、認証など、IIS の必要以上の機能は含まれていません。  
  
    -   このサーバーでは、データ サービスから大きなバイナリ データにアクセスするときに [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントによって既定で送信されるチャンク HTTP ストリームを処理できません。 詳細については、「[ストリーミング プロバイダー](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)」を参照してください。  
  
    -   このサーバーでは、キー値で `.` がピリオド \([!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]\) 文字をサポートしている場合でも、URL のピリオド文字を適切に処理できません。  
  
    > [!TIP]
    >  開発時に [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 開発サーバーを使用してデータ サービスをテストできる場合でも、IIS を実行する Web サーバーに配置した後でデータ サービスを再度テストする必要があります。  
  
3.  **Microsoft Azure 開発環境**  
  
     Microsoft Azure Tools for [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] には、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で Microsoft Azure サービスを開発するためのツールの統合セットが含まれています。 これらのツールでは、Microsoft Azure に配置できるデータ サービスを開発し、配置前にローカル コンピューターでデータ サービスをテストすることができます。[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を使用して Microsoft Azure プラットフォームで実行されるデータ サービスを開発する場合は、これらのツールを使用してください。 Microsoft Azure Tools for [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] は、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=201848)からダウンロードできます。 Microsoft Azure 上で実行されるデータ サービスの開発の[!INCLUDE[crabout](../../../../includes/crabout-md.md)]については、ブログの記事「[Deploying an OData Service in Microsoft Azure \(Microsoft Azure での OData サービスの配置\)](http://go.microsoft.com/fwlink/?LinkId=201847)」を参照してください。  
  
### 開発のヒント  
 データ サービスを開発する際は、次の点を考慮してください。  
  
-   ユーザーを認証する場合や、特定のユーザーのアクセスを制限する場合は、データ サービスのセキュリティ要件を決定します。 詳細については、「[WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。  
  
-   データ サービスをデバッグするときは、HTTP 検査プログラムを使用すると、要求メッセージおよび応答メッセージの内容を検査できるので非常に便利です。 生のパケットを表示できるネットワーク パケット アナライザーを使用すると、データ サービスの HTTP 要求および HTTP 応答を検査できます。  
  
-   データ サービスのデバッグ時は、通常の操作時以上に、データ サービスの詳細なエラー情報が必要になることがあります。 データ サービスから詳細なエラー情報を取得するには、<xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> の <xref:System.Data.Services.DataServiceConfiguration> プロパティを `true` に設定し、データ サービス クラスの <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> 属性の <xref:System.ServiceModel.Description.ServiceDebugBehavior> プロパティを `true` に設定します。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Debugging WCF Data Services \(WCF Data Services のデバッグ\)](http://go.microsoft.com/fwlink/?LinkId=201868)」を参照してください。 また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でトレースを有効にして、HTTP メッセージング レイヤーで発生した例外を表示することもできます。 詳細については、「[トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)」を参照してください。  
  
-   データ サービスは、通常、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーション プロジェクトとして開発されますが、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web サイト プロジェクトとしてデータ サービスを作成することもできます。 この 2 種類のプロジェクトの違いについては、「[Web Application Projects versus Web Site Projects in Visual Studio \(Visual Studio での Web アプリケーション プロジェクトと Web サイト プロジェクト\)](http://msdn.microsoft.com/ja-jp/2861815e-f5a2-4378-a2f8-b8a86dc012f5)」を参照してください。  
  
-   [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] の **\[新しい項目の追加\]** ダイアログ ボックスを使用してデータ サービスを作成すると、そのデータ サービスは IIS の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] でホストされます。[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] と IIS がデータ サービスの既定のホストですが、その他のホスト オプションもサポートされています。 詳細については、「[データ サービスのホスティング](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)」を参照してください。  
  
## WCF Data Services の配置  
 WCF Data Services では、データ サービスをホストするプロセスを柔軟に選択できます。[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を使用して、次のプラットフォームにデータ サービスを配置できます。  
  
-   **IIS でホストされる Web サーバー**  
  
     データ サービスを [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトとして開発すると、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の標準配置プロセスを使用して IIS Web サーバーに配置することができます。[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] は、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 向けに、配置するデータ サービスをホストする [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトの種類に応じて次の配置テクノロジを提供します。  
  
    -   **ASP.NET Web アプリケーション用の配置テクノロジ**  
  
        -   [Web 配置パッケージ](http://msdn.microsoft.com/ja-jp/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [ワンクリック発行機能](http://msdn.microsoft.com/ja-jp/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **ASP.NET Web サイト用の配置テクノロジ**  
  
        -   [Web サイトのコピー ツール](../Topic/How%20to:%20Deploy%20a%20Web%20Site%20Project%20by%20using%20the%20Copy%20Web%20Site%20Tool.md)  
  
        -   [Web サイトの発行ツール](../Topic/How%20to:%20Deploy%20a%20Web%20Site%20Project%20by%20Using%20the%20Publish%20Web%20Site%20Tool.md)  
  
        -   [XCopy](../Topic/Walkthrough:%20Deploying%20a%20Web%20Site%20Project%20by%20Using%20XCOPY.md)  
  
     [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションの配置オプションの[!INCLUDE[crabout](../../../../includes/crabout-md.md)]については、「[Web Deployment Overview for Visual Studio and ASP.NET \(Visual Studio と ASP.NET の Web 配置の概要\)](http://msdn.microsoft.com/ja-jp/99bd1927-b59f-4e02-87b4-55c6ba2adbc3)」を参照してください。  
  
    > [!TIP]
    >  データ サービスを IIS に配置する前に、IIS を実行している Web サーバーへの配置をテストしておく必要があります。 詳細については、「[方法: IIS 上で実行する WCF Data Service を開発する](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。  
  
-   **Windows Azure**  
  
     Microsoft Azure Tools for [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] を使用して、データ サービスを Microsoft Azure に配置できます。 Microsoft Azure Tools for [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] は、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=201848)からダウンロードできます。 Microsoft Azure へのデータ サービスの配置の[!INCLUDE[crabout](../../../../includes/crabout-md.md)]については、ブログの記事「[Deploying an OData Service in Windows Azure \(Microsoft Azure での OData サービスの配置\)](http://go.microsoft.com/fwlink/?LinkId=201847)」を参照してください。  
  
### 配置に関する注意事項  
 データ サービスを配置する際は、次の点を考慮してください。  
  
-   [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロバイダーを使用して SQL Server データベースにアクセスするデータ サービスを配置する場合、データ サービスの配置でのデータ構造、データ、またはその両方の反映も必要になることがあります。[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] では対象データベースでこの操作を行うスクリプト \(.sql ファイル\) を自動的に作成することができ、これらのスクリプトを [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションの Web 配置パッケージに含めることができます。 詳細については、「[方法: Web アプリケーション プロジェクトと共にデータベースを配置する](http://msdn.microsoft.com/ja-jp/683b33f1-8a3d-45cf-af6e-61ab50fc518b)」を参照してください。[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サイトの場合は、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] の **\[データベースの発行\]** ウィザードを使用してこの操作を実行できます。 詳細については、「[Deploying a Database by Using the Database Publishing Wizard](../Topic/Deploying%20a%20Database%20by%20Using%20the%20Database%20Publishing%20Wizard.md)」を参照してください。  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の実装が含まれているので、Windows Server AppFabric を使用して、Windows Server で実行されている IIS に配置されたデータ サービスを監視できます。 Server AppFabric を使用したデータ サービスの監視の[!INCLUDE[crabout](../../../../includes/crabout-md.md)]については、ブログの記事「[Tracking WCF Data Services with Windows Server AppFabric \(Windows Server AppFabric による WCF Data Services の追跡\)](http://go.microsoft.com/fwlink/?LinkID=202005)」を参照してください。  
  
## 参照  
 [データ サービスのホスティング](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)   
 [WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)   
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)