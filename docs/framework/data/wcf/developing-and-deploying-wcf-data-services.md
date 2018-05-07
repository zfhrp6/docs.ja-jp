---
title: WCF Data Services の開発と配置
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: e02b7317eef8e7124bd5ba9ceef201cddc9bbea1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="developing-and-deploying-wcf-data-services"></a>WCF Data Services の開発と配置
このトピックでは、 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]の開発と配置について説明します。 複数の基本情報については[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]を参照してください[作業の開始](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)と[概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)です。  
  
## <a name="developing-wcf-data-services"></a>WCF Data Services の開発  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用して、 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]をサポートするデータ サービスを作成する場合、開発時に次の基本的なタスクを実行する必要があります。  
  
1.  **データ モデルを定義する**  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、リレーショナル データベースから遅延バインディング データ型に至るさまざまなデータ ソースのデータに基づいてデータ モデルを定義できるようにする各種のデータ サービス プロバイダーをサポートしています。 詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)です。  
  
2.  **データ サービスを作成する**  
  
     最も基本的なデータ サービスでは、 <xref:System.Data.Services.DataService%601> クラスを継承するクラスを `T` 型 (エンティティ コンテナーの名前空間修飾名) と一緒に公開します。 詳細については、「 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)の開発と配置について説明します。  
  
3.  **データ サービスを構成する**  
  
     既定では、 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、エンティティ コンテナーによって公開されているリソースへのアクセスは無効になります。 <xref:System.Data.Services.DataServiceConfiguration> インターフェイスを使用すると、リソースとサービス操作へのアクセスの構成、サポートされる [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]のバージョンの指定、およびサービス全体のその他の動作 (バッチ動作や 1 つの応答フィードで返すことができるエンティティの最大数など) を定義できます。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)です。  
  
 このトピックでは、Visual Studio を使用して、主に、開発とデータ サービスの展開について説明します。 データを [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] フィードとして公開できるようにする [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の柔軟性については、「 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)の開発と配置について説明します。  
  
### <a name="choosing-a-development-web-server"></a>開発 Web サーバーの選択  
 として WCF データ サービスを開発する際に、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]アプリケーションまたは[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Visual Studio を使用して Web サイトがある開発時に、データ サービスを実行する対象の Web サーバーを選択します。 次の Web サーバーは、テストし、ローカル コンピューターでデータ サービスのデバッグを容易にできるように Visual Studio と統合します。  
  
1.  **ローカル IIS サーバー**  
  
     インターネット インフォメーション サービス (IIS) で実行される [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションまたは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サイトとしてデータ サービスを作成する場合は、ローカル コンピューターで IIS を使用してデータ サービスを開発およびテストすることをお勧めします。 IIS でデータ サービスを実行すると、デバッグ時における HTTP 要求のトレースが容易になります。 また、データ サービスに必要なファイルやデータベースなどのリソースにアクセスするために IIS で必要とされる権限を事前に確認することもできます。 IIS で、データ サービスを実行する必要がありますにより、IIS と Windows Communication Foundation (WCF) の両方がインストールされ、正しく構成されていることを確認しており、ファイル システムおよびデータベースで IIS アカウントへのアクセスを付与します。 詳細については、「 [方法: IIS 上で実行する WCF Data Service を開発する](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。  
  
    > [!NOTE]
    >  ローカル IIS サーバーを構成する開発環境を有効にする管理者権限を持つ Visual Studio を実行する必要があります。  
  
2.  **Visual Studio 開発サーバー**  
  
     Visual Studio には、Visual Studio 開発サーバーを使用して、組み込みの Web サーバーが含まれています。 これは既定の Web サーバーを[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクト。 この Web サーバーは、開発時にローカル コンピューターで [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトを実行するように設計されています。 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)Visual Studio 開発サーバーで実行されているデータ サービスを作成する方法を示します。  
  
     Visual Studio 開発サーバーを使用してデータ サービスを開発する場合、次の制限事項の注意する必要があります。  
  
    -   このサーバーにはローカル コンピューター上でしかアクセスできません。  
  
    -   このサーバーは、HTTP メッセージの既定のポートであるポート 80 ではなく、 `localhost` および特定のポートでリッスンします。 詳細については、「 [ASP.NET Web プロジェクト用の Visual Studio の Web サーバー](http://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328)」を参照してください。  
  
    -   このサーバーでは、現在のユーザー アカウントのコンテキストでデータ サービスが実行されます。 たとえば、管理者レベルのユーザーとして実行している場合、Visual Studio 開発サーバーで実行されているデータ サービスは管理者レベルの特権があります。 そのため、データ サービスは、IIS サーバーに配置されたときにはアクセスする権限を持たないリソースにも、アクセスできることになります。  
  
    -   このサーバーには、認証など、IIS の必要以上の機能は含まれていません。  
  
    -   このサーバーでは、データ サービスから大きなバイナリ データにアクセスするときに [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントによって既定で送信されるチャンク HTTP ストリームを処理できません。 詳細については、次を参照してください。[ストリーミング プロバイダー](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)です。  
  
    -   このサーバーでは、キー値で`.`がピリオド ( [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ) 文字をサポートしている場合でも、URL のピリオド文字を適切に処理できません。  
  
    > [!TIP]
    >  場合でも、Visual Studio 開発サーバーを使用すると、開発時にデータ サービスをテスト、IIS を実行している Web サーバーに配置した後にもう一度テストする必要があります。  
  
3.  **Microsoft Azure 開発環境**  
  
     Windows Azure Tools for Visual Studio には、Visual Studio での Windows Azure サービスを開発するためのツールの統合セットが含まれています。 これらのツールでは、Microsoft Azure に配置できるデータ サービスを開発し、配置前にローカル コンピューターでデータ サービスをテストすることができます。 Visual Studio を使用して、Windows Azure プラットフォームで実行されているデータ サービスを開発する場合は、これらのツールを使用します。 Visual Studio からの Windows Azure Tools をダウンロードすることができます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=201848)です。 Windows Azure で実行されているデータ サービスの開発に関する詳細については、投稿をご覧ください。 [Windows Azure で OData サービスを展開する](http://go.microsoft.com/fwlink/?LinkId=201847)です。  
  
### <a name="development-tips"></a>開発のヒント  
 データ サービスを開発する際は、次の点を考慮してください。  
  
-   ユーザーを認証する場合や、特定のユーザーのアクセスを制限する場合は、データ サービスのセキュリティ要件を決定します。 詳細については、「 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。  
  
-   データ サービスをデバッグするときは、HTTP 検査プログラムを使用すると、要求メッセージおよび応答メッセージの内容を検査できるので非常に便利です。 生のパケットを表示できるネットワーク パケット アナライザーを使用すると、データ サービスの HTTP 要求および HTTP 応答を検査できます。  
  
-   データ サービスのデバッグ時は、通常の操作時以上に、データ サービスの詳細なエラー情報が必要になることがあります。 データ サービスから詳細なエラー情報を取得するには、 <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> の <xref:System.Data.Services.DataServiceConfiguration> プロパティを `true` に設定し、データ サービス クラスの <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> 属性の <xref:System.ServiceModel.Description.ServiceDebugBehavior> プロパティを `true`に設定します。 詳細については、投稿をご覧ください。 [WCF Data Services のデバッグ](http://go.microsoft.com/fwlink/?LinkId=201868)です。 また、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でトレースを有効にして、HTTP メッセージング レイヤーで発生した例外を表示することもできます。 詳細については、「 [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)」を参照してください。  
  
-   データ サービスは通常として開発、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]アプリケーション プロジェクトができますもサービスを作成するデータとして、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Visual Studio での Web サイト プロジェクト。 2 種類のプロジェクト間の相違点については、次を参照してください。 [NIB: Web アプリケーション プロジェクトと Visual Studio での Web サイト プロジェクト](http://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5)です。  
  
-   使用してデータ サービスを作成する場合、**新しい項目の追加**Visual Studio で、データ サービス ダイアログ ボックスがによってホストされている[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]IIS でします。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] と IIS がデータ サービスの既定のホストですが、その他のホスト オプションもサポートされています。 詳細については、次を参照してください。[データ サービスのホスティング](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)です。  
  
## <a name="deploying-wcf-data-services"></a>WCF Data Services の配置  
 WCF Data Services では、データ サービスをホストするプロセスを柔軟に選択できます。 Visual Studio を使用すると、次のプラットフォームにデータ サービスを配置します。  
  
-   **IIS でホストされる Web サーバー**  
  
     データ サービスを [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] プロジェクトとして開発すると、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の標準配置プロセスを使用して IIS Web サーバーに配置することができます。  Visual Studio には、次の展開テクノロジの[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]種類に応じての[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]を展開しているデータ サービスをホストするプロジェクトです。  
  
    -   **ASP.NET Web アプリケーション用の配置テクノロジ**  
  
        -   [Web 配置パッケージ](http://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [ワンクリック発行機能](http://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **ASP.NET Web サイト用の配置テクノロジ**  
  
        -   [Web サイトのコピー ツール](http://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)  
  
        -   [Web サイトの発行ツール](http://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)  
  
        -   [XCopy](http://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)  
  
     配置オプションの詳細については、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]アプリケーションを参照してください[for Visual Studio と ASP.NET Web 配置の概要](http://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3)です。  
  
    > [!TIP]
    >  データ サービスを IIS に配置する前に、IIS を実行している Web サーバーへの配置をテストしておく必要があります。 詳細については、「 [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。  
  
-   **Windows Azure**  
  
     Visual Studio の Windows Azure Tools を使用して、Windows Azure にデータ サービスを展開できます。 Visual Studio からの Windows Azure Tools をダウンロードすることができます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=201848)です。 Windows Azure へのデータ サービスの展開に関する詳細については、投稿をご覧ください。 [Windows Azure で OData サービスを展開する](http://go.microsoft.com/fwlink/?LinkId=201847)です。  
  
### <a name="deployment-considerations"></a>配置に関する注意事項  
 データ サービスを配置する際は、次の点を考慮してください。  
  
-   [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロバイダーを使用して SQL Server データベースにアクセスするデータ サービスを配置する場合、データ サービスの配置でのデータ構造、データ、またはその両方の反映も必要になることがあります。 Visual Studio がこれを行うレプリケーション先データベースのスクリプト (.sql ファイル) を自動的に作成し、これらのスクリプトは、の Web 配置パッケージに含めることができます、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]アプリケーションです。 詳細については、次を参照してください。 [NIB: 方法: Web アプリケーション プロジェクトでのデータベースを配置](http://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b)です。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サイト、こうことを使用して、 **Database Publishing Wizard** Visual Studio でします。 詳細については、「 [Deploying a Database by Using the Database Publishing Wizard](http://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7)」を参照してください。  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の実装が含まれているので、Windows Server AppFabric を使用して、Windows Server で実行されている IIS に配置されたデータ サービスを監視できます。 Windows Server AppFabric を使用してデータ サービスを監視する方法の詳細については、投稿をご覧ください。 [Windows Server AppFabric で WCF データ サービスを追跡](http://go.microsoft.com/fwlink/?LinkID=202005)です。  
  
## <a name="see-also"></a>関連項目  
 [データ サービスのホスティング](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 [WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
