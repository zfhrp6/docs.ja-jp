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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6ba18a1823386042a3aaf61cffac357871eca294
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="aceda-102">方法: IIS 上で実行する WCF Data Service を開発する</span><span class="sxs-lookup"><span data-stu-id="aceda-102">How to: Develop a WCF Data Service Running on IIS</span></span>
<span data-ttu-id="aceda-103">このトピックは、使用する方法を示します[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]でインターネット インフォメーション サービス (IIS) を実行している ASP.NET Web アプリケーションによってホストされる Northwind サンプル データベースに基づくデータ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="aceda-103">This topic shows how to use [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="aceda-104">ASP.NET 開発サーバーで実行されている ASP.NET Web アプリケーションとして同じ Northwind データ サービスを作成する方法の例は、次を参照してください。、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="aceda-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aceda-105">Northwind データ サービスを作成するには、ローカル コンピューターに Northwind サンプル データベースをインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="aceda-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="aceda-106">このサンプル データベースをダウンロードするには、ダウンロード ページ「 [SQL Server 用サンプル データベース](http://go.microsoft.com/fwlink/?linkid=24758)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aceda-106">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
 <span data-ttu-id="aceda-107">このトピックでは、Entity Framework プロバイダーを使用してデータ サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="aceda-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="aceda-108">その他のデータ サービス プロバイダーを利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="aceda-108">Other data services providers are available.</span></span> <span data-ttu-id="aceda-109">詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="aceda-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="aceda-110">サービスを作成した後に、データ サービス リソースへのアクセスを明示的に提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aceda-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="aceda-111">詳細については、次を参照してください。[する方法: データ サービスへのアクセスの有効化](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="aceda-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="aceda-112">IIS 上で実行する ASP.NET Web アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="aceda-112">To create the ASP.NET Web application that runs on IIS</span></span>  
  
1.  <span data-ttu-id="aceda-113">Visual Studio での**ファイル**メニューの **新規**、し、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-113">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="aceda-114">**新しいプロジェクト** ダイアログ ボックスで、プログラミング言語と Visual Basic または Visual c# のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="aceda-114">In the **New Project** dialog box, select either Visual Basic or Visual C# as the programming language.</span></span>  
  
3.  <span data-ttu-id="aceda-115">**テンプレート**ペインで、 **ASP.NET Web アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-115">In the **Templates** pane, select **ASP.NET Web Application**.</span></span> <span data-ttu-id="aceda-116">メモ : Visual Studio Web Developer を使用する場合は、新しい Web アプリケーションではなく、新しい Web サイトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aceda-116">Note: If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
4.  <span data-ttu-id="aceda-117">型`NorthwindService`として、プロジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="aceda-117">Type `NorthwindService` as the name of the project.</span></span>  
  
5.  <span data-ttu-id="aceda-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aceda-118">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="aceda-119">**プロジェクト**メニューの  **NorthwindService プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>  
  
7.  <span data-ttu-id="aceda-120">選択、 **Web** 、タブをクリックし**ローカル IIS Web サーバー**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>  
  
8.  <span data-ttu-id="aceda-121">をクリックして**仮想ディレクトリの作成** をクリックし、 **OK**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-121">Click **Create Virtual Directory** and then click **OK**.</span></span>  
  
9. <span data-ttu-id="aceda-122">管理特権を持つコマンド プロンプトから、次のコマンドを実行します (オペレーティング システムによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="aceda-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="aceda-123">32 ビット システム: </span><span class="sxs-lookup"><span data-stu-id="aceda-123">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   <span data-ttu-id="aceda-124">64 ビット システム: </span><span class="sxs-lookup"><span data-stu-id="aceda-124">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     <span data-ttu-id="aceda-125">これにより、コンピューターに Windows Communication Foundation (WCF) が登録されます。</span><span class="sxs-lookup"><span data-stu-id="aceda-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>  
  
10. <span data-ttu-id="aceda-126">管理特権を持つコマンド プロンプトから、次のコマンドを実行します (オペレーティング システムによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="aceda-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="aceda-127">32 ビット システム: </span><span class="sxs-lookup"><span data-stu-id="aceda-127">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   <span data-ttu-id="aceda-128">64 ビット システム: </span><span class="sxs-lookup"><span data-stu-id="aceda-128">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     <span data-ttu-id="aceda-129">これにより、WCF がコンピューターにインストールされた後、IIS は正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="aceda-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="aceda-130">IIS の再起動が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aceda-130">You might have to also restart IIS.</span></span>  
  
11. <span data-ttu-id="aceda-131">ASP.NET アプリケーションが IIS7 で実行されると、次の手順も実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aceda-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="aceda-132">IIS マネージャーを開きの下にある PhotoService アプリケーションに移動**Default Web Site**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="aceda-133">**機能ビュー**をダブルクリックして**認証**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-133">In **Features View**, double-click **Authentication**.</span></span>  
  
    3.  <span data-ttu-id="aceda-134">**認証**] ページで、[**匿名認証**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>  
  
    4.  <span data-ttu-id="aceda-135">**アクション** ウィンドウで、をクリックして**編集**を設定するセキュリティ プリンシパルを匿名ユーザーの下、サイトに接続します。</span><span class="sxs-lookup"><span data-stu-id="aceda-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>  
  
    5.  <span data-ttu-id="aceda-136">**匿名認証資格情報の編集**ダイアログ ボックスで、**アプリケーション プール id**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="aceda-137">ネットワーク サービス アカウントを使用する際、そのアカウントに関連するすべての内部ネットワーク アクセス権を匿名ユーザーに付与します。</span><span class="sxs-lookup"><span data-stu-id="aceda-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>  
  
12. <span data-ttu-id="aceda-138">SQL Server Management Studio、sqlcmd.exe ユーティリティ、または Visual Studio の Transact-SQL エディターを使用して、Northwind データベースがアタッチされた SQL Server のインスタンスに対して次の Transact-SQL コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="aceda-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     <span data-ttu-id="aceda-139">これにより、IIS の実行に使用される Windows アカウントに対して、SQL Server インスタンスのログインが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aceda-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="aceda-140">IIS は、これを使用して SQL Server インスタンスに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="aceda-140">This enables IIS to connect to the SQL Server instance.</span></span>  
  
13. <span data-ttu-id="aceda-141">Northwind データベースをアタッチして、次の Transact-SQL コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="aceda-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>  
  
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
  
     <span data-ttu-id="aceda-142">これにより、新しいログインに権限が付与され、IIS は Northwind データベースに対してデータの読み取りおよび書き込みを行うことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="aceda-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="aceda-143">データ モデルを定義するには</span><span class="sxs-lookup"><span data-stu-id="aceda-143">To define the data model</span></span>  
  
1.  <span data-ttu-id="aceda-144">**ソリューション エクスプ ローラー**を ASP.NET プロジェクトの名前を右クリックし、をクリックして**新しい項目の追加。**</span><span class="sxs-lookup"><span data-stu-id="aceda-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="aceda-145">**新しい項目の追加**ダイアログ ボックスで、 **ADO.NET エンティティ データ モデル**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="aceda-146">データ モデルの名前を入力`Northwind.edmx`です。</span><span class="sxs-lookup"><span data-stu-id="aceda-146">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="aceda-147">エンティティ データ モデル ウィザードで、次のように選択します。**データベースから生成**、クリックして**次**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="aceda-148">次の手順のいずれかの手順を実行して、データ モデルをデータベースに接続し、をクリックして**次**:</span><span class="sxs-lookup"><span data-stu-id="aceda-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="aceda-149">データベース接続が既に構成されていない場合にクリックして**新しい接続**し、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="aceda-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="aceda-150">詳細については、次を参照してください。[する方法: SQL Server データベースへの接続の作成](http://go.microsoft.com/fwlink/?LinkId=123631)です。</span><span class="sxs-lookup"><span data-stu-id="aceda-150">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="aceda-151">この [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="aceda-151">This [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="aceda-152">\- または</span><span class="sxs-lookup"><span data-stu-id="aceda-152">\- or -</span></span>  
  
    -   <span data-ttu-id="aceda-153">Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="aceda-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="aceda-154">ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="aceda-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="aceda-155">をクリックして**完了**ウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="aceda-155">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aceda-156">この生成されたデータ モデルは、エンティティ型の外部キー プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="aceda-156">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="aceda-157">Visual Studio 2008 を使用して作成したデータ モデルには、これらの外部キー プロパティが含まれません。</span><span class="sxs-lookup"><span data-stu-id="aceda-157">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="aceda-158">そのため、Visual Studio 2008 を使用して作成された Northwind データ サービスにアクセスしようとする前に、このバージョンの Northwind データ サービスにアクセスするために作成されたクライアント アプリケーションのクライアント データ サービス クラスを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aceda-158">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="aceda-159">データ サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="aceda-159">To create the data service</span></span>  
  
1.  <span data-ttu-id="aceda-160">**ソリューション エクスプ ローラー**、ASP.NET プロジェクトの名前を右クリックし、クリックして**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-160">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="aceda-161">**新しい項目の追加**ダイアログ ボックスで、 **ADO.NET データ サービス**です。</span><span class="sxs-lookup"><span data-stu-id="aceda-161">In the **Add New Item** dialog box, select **ADO.NET Data Service**.</span></span>  
  
3.  <span data-ttu-id="aceda-162">サービスの名前を入力`Northwind`です。</span><span class="sxs-lookup"><span data-stu-id="aceda-162">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="aceda-163">Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aceda-163">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="aceda-164">既定では、コード エディターのウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="aceda-164">By default, the code-editor window opens.</span></span> <span data-ttu-id="aceda-165">**ソリューション エクスプローラー**では、このサービスに Northwind という名前が付き、拡張子は .svc.cs または .svc.vb になります。</span><span class="sxs-lookup"><span data-stu-id="aceda-165">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="aceda-166">データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindEntities`) で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="aceda-166">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="aceda-167">クラス定義は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="aceda-167">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a><span data-ttu-id="aceda-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="aceda-168">See Also</span></span>  
 [<span data-ttu-id="aceda-169">サービスとしてのデータの公開</span><span class="sxs-lookup"><span data-stu-id="aceda-169">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
