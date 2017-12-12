---
title: "データ サービスの作成"
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
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22fc561d7df9bbd81bf19d351af2d07bc6b51237
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="creating-the-data-service"></a><span data-ttu-id="a1b00-102">データ サービスの作成</span><span class="sxs-lookup"><span data-stu-id="a1b00-102">Creating the Data Service</span></span>
<span data-ttu-id="a1b00-103">このタスクを使用するサンプル データ サービスを作成する[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]を公開する、 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Northwind サンプル データベースに基づいているフィード。</span><span class="sxs-lookup"><span data-stu-id="a1b00-103">In this task, you will create a sample data service that uses [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that is based on the Northwind sample database.</span></span> <span data-ttu-id="a1b00-104">このタスクに必要な基本手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a1b00-104">The task involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="a1b00-105">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-105">Create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span>  
  
2.  <span data-ttu-id="a1b00-106">[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ツールを使用して、データ モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-106">Define the data model by using the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] tools.</span></span>  
  
3.  <span data-ttu-id="a1b00-107">データ サービスを Web アプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-107">Add the data service to the Web application.</span></span>  
  
4.  <span data-ttu-id="a1b00-108">データ サービスへのアクセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a1b00-108">Enable access to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1b00-109">このタスクを完了するときに作成する [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] で提供される [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 開発サーバー上で実行します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-109">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application that you create when you complete this task runs on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server provided by [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="a1b00-110"> 開発サーバーは、ローカル コンピューターからのアクセスのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a1b00-110"> Development Server only supports access from the local computer.</span></span> <span data-ttu-id="a1b00-111">開発時にデータ サービスのテストおよびトラブルシューティングを行いやすくするためにも、インターネット インフォメーション サービス (IIS) を使用して、データ サービスをホストするアプリケーションを実行することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1b00-111">To also make it easier to test and troubleshoot the data service during development, consider running the application that hosts the data service by using Internet Information Services (IIS).</span></span> <span data-ttu-id="a1b00-112">詳細については、「 [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1b00-112">For more information, see [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application"></a><span data-ttu-id="a1b00-113">ASP.NET Web アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="a1b00-113">To create the ASP.NET Web application</span></span>  
  
1.  <span data-ttu-id="a1b00-114">[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]の**ファイル**メニューの **新規**、し、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-114">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="a1b00-115">**新しいプロジェクト** ダイアログ ボックスで、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]または[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]選択、 **Web**テンプレート、および選択**ASP.NET Web アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-115">In the **New Project** dialog box, under either [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] select the **Web** template, and then select **ASP.NET Web Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1b00-116">[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer を使用する場合は、新しい Web アプリケーションではなく新しい Web サイトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1b00-116">If you use [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
3.  <span data-ttu-id="a1b00-117">型`NorthwindService`として、プロジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="a1b00-117">Type `NorthwindService` as the name of the project.</span></span>  
  
4.  <span data-ttu-id="a1b00-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1b00-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="a1b00-119">(省略可能) Web アプリケーションに対して特定のポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-119">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="a1b00-120">メモ: このクイック スタートの以降の作業では、ポート番号 `12345` を使用します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-120">Note: the port number `12345` is used in the rest of the quickstart.</span></span>  
  
    1.  <span data-ttu-id="a1b00-121">**ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトだけが作成されると、クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-121">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project that you just created, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="a1b00-122">選択、 **Web**タブをクリックしの値を設定、**特定のポート**テキスト ボックスに`12345`です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-122">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="a1b00-123">データ モデルを定義するには</span><span class="sxs-lookup"><span data-stu-id="a1b00-123">To define the data model</span></span>  
  
1.  <span data-ttu-id="a1b00-124">**ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトをクリックして**新しい項目の追加。**</span><span class="sxs-lookup"><span data-stu-id="a1b00-124">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="a1b00-125">**新しい項目の追加**ダイアログ ボックスで、をクリックして、**データ**クリックしてテンプレート**ADO.NET エンティティ データ モデル**です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-125">In the **Add New Item** dialog box, click the **Data** template and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="a1b00-126">データ モデルの名前を入力`Northwind.edmx`です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-126">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="a1b00-127">[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]ウィザードで、**データベースから生成**、順にクリック**次**です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-127">In the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="a1b00-128">次の手順のいずれかの手順を実行して、データ モデルをデータベースに接続し、をクリックして**次**:</span><span class="sxs-lookup"><span data-stu-id="a1b00-128">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="a1b00-129">データベース接続が既に構成されていない場合にクリックして**新しい接続**し、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-129">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="a1b00-130">詳細については、次を参照してください。[する方法: SQL Server データベースへの接続の作成](http://go.microsoft.com/fwlink/?LinkId=123631)です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-130">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="a1b00-131">この [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1b00-131">This [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="a1b00-132">\- または</span><span class="sxs-lookup"><span data-stu-id="a1b00-132">\- or -</span></span>  
  
    -   <span data-ttu-id="a1b00-133">Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-133">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="a1b00-134">ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="a1b00-134">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="a1b00-135">をクリックして**完了**ウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a1b00-135">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1b00-136">この生成されたデータ モデルは、エンティティ型の外部キー プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="a1b00-136">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="a1b00-137">[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 を使用して作成したデータ モデルには、これらの外部キー プロパティが含まれません。</span><span class="sxs-lookup"><span data-stu-id="a1b00-137">Data models created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="a1b00-138">そのため、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 を使用して作成された Northwind データ サービスにアクセスしようとする前に、このバージョンの Northwind データ サービスにアクセスするために作成されたクライアント アプリケーションのクライアント データ サービス クラスを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1b00-138">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="a1b00-139">データ サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="a1b00-139">To create the data service</span></span>  
  
1.  <span data-ttu-id="a1b00-140">**ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトをクリックして**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-140">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="a1b00-141">**新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-141">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="a1b00-142">サービスの名前を入力`Northwind`です。</span><span class="sxs-lookup"><span data-stu-id="a1b00-142">For the name of the service, type `Northwind`.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="a1b00-143">Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a1b00-143">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="a1b00-144">既定では、コード エディターのウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="a1b00-144">By default, the code-editor window opens.</span></span> <span data-ttu-id="a1b00-145">**ソリューション エクスプ ローラー**サービスの名前は、Northwind、拡張子を持つ。 svc.cs または.svc.vb になります。</span><span class="sxs-lookup"><span data-stu-id="a1b00-145">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="a1b00-146">データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindEntities`) で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a1b00-146">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="a1b00-147">クラス定義は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a1b00-147">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a><span data-ttu-id="a1b00-148">データ サービス リソースへのアクセスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="a1b00-148">To enable access to data service resources</span></span>  
  
1.  <span data-ttu-id="a1b00-149">データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a1b00-149">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="a1b00-150">これにより、承認されたクライアントは、指定したエンティティ セットのリソースに読み取りおよび書き込みアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="a1b00-150">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1b00-151">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a1b00-151">Any client that can access the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="a1b00-152">運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1b00-152">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="a1b00-153">詳細については、「 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1b00-153">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a1b00-154">次の手順</span><span class="sxs-lookup"><span data-stu-id="a1b00-154">Next Steps</span></span>  
 <span data-ttu-id="a1b00-155">公開する新しいデータ サービスが正常に作成、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]に対する権限があるクライアントからフィードへのアクセスを有効にして、Northwind サンプル データベースに基づいてフィード、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="a1b00-155">You have successfully created a new data service that exposes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span> <span data-ttu-id="a1b00-156">データ サービスを開始する次に、[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]アクセスして、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web ブラウザーから HTTP GET 要求を送信してフィードします。</span><span class="sxs-lookup"><span data-stu-id="a1b00-156">Next, you will start the data service from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by submitting HTTP GET requests through a Web browser:</span></span>  
  
 [<span data-ttu-id="a1b00-157">Web ブラウザーからサービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a1b00-157">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="a1b00-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1b00-158">See Also</span></span>  
 [<span data-ttu-id="a1b00-159">ADO.NET Entity Data Model ツール</span><span class="sxs-lookup"><span data-stu-id="a1b00-159">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
