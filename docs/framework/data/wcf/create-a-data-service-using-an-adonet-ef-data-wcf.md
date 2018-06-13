---
title: '方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 95439e2f73350e8f67aff61de7a97d80410109ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365697"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="4695f-102">方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="4695f-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="4695f-103"> では、エンティティ データはデータ サービスとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="4695f-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="4695f-104">このエンティティのデータがによって提供される、 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]データ ソースがリレーショナル データベースの場合。</span><span class="sxs-lookup"><span data-stu-id="4695f-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="4695f-105">このトピックは、作成する方法を示します、 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-ベースの既存のデータベースに基づいており、このデータ モデルを使用して新しいデータ サービスを作成する Visual Studio の Web アプリケーションでデータ モデル。</span><span class="sxs-lookup"><span data-stu-id="4695f-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>  
  
 <span data-ttu-id="4695f-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]も生成できるコマンド ライン ツールを提供する[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]Visual Studio プロジェクトの外側でモデル。</span><span class="sxs-lookup"><span data-stu-id="4695f-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a Visual Studio project.</span></span> <span data-ttu-id="4695f-107">詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルの生成に使用する EdmGen.exe](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)です。</span><span class="sxs-lookup"><span data-stu-id="4695f-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="4695f-108">既存のデータベースに基づく Entity Framework モデルを既存の Web アプリケーションに追加するには</span><span class="sxs-lookup"><span data-stu-id="4695f-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>  
  
1.  <span data-ttu-id="4695f-109">**プロジェクト** メニューのをクリックして**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="4695f-109">On the **Project** menu, click **Add new item**.</span></span>  
  
2.  <span data-ttu-id="4695f-110">**テンプレート** ウィンドウで、をクリックして、**データ**カテゴリ、および選択**ADO.NET エンティティ データ モデル**です。</span><span class="sxs-lookup"><span data-stu-id="4695f-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="4695f-111">モデルの名前を入力し、クリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="4695f-111">Type the model name and then click **Add**.</span></span>  
  
     <span data-ttu-id="4695f-112">[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ウィザードの最初のページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4695f-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>  
  
4.  <span data-ttu-id="4695f-113">**モデルのコンテンツ**ダイアログ ボックスで、**データベースから生成**です。</span><span class="sxs-lookup"><span data-stu-id="4695f-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="4695f-114">その後、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4695f-114">Then click **Next**.</span></span>  
  
5.  <span data-ttu-id="4695f-115">クリックして、**新しい接続**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4695f-115">Click the **New Connection** button.</span></span>  
  
6.  <span data-ttu-id="4695f-116">**接続プロパティ**ダイアログ ボックスで、サーバー名を入力、認証方法を選択して、データベース名を入力および順にクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="4695f-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4695f-117">**データ接続の選択**データベース接続の設定 ダイアログ ボックスを更新します。</span><span class="sxs-lookup"><span data-stu-id="4695f-117">The **Choose Your Data Connection**s dialog box is updated with your database connection settings.</span></span>  
  
7.  <span data-ttu-id="4695f-118">いることを確認、**エンティティ接続設定を付けて App.Config に保存します。** チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="4695f-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="4695f-119">その後、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4695f-119">Then click **Next**.</span></span>  
  
8.  <span data-ttu-id="4695f-120">**データベース オブジェクトの選択**ダイアログ ボックスで、すべてのデータベースのオブジェクトがデータ サービスの公開を計画することです。</span><span class="sxs-lookup"><span data-stu-id="4695f-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4695f-121">データ モデルに含まれるオブジェクトは、データ サービスによって自動的には公開されません。</span><span class="sxs-lookup"><span data-stu-id="4695f-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="4695f-122">これらのオブジェクトは、サービス自身によって明示的に公開される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4695f-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="4695f-123">詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="4695f-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
9. <span data-ttu-id="4695f-124">をクリックして**完了**ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="4695f-124">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="4695f-125">特定のデータベースに基づく既定のデータ モデルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4695f-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="4695f-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] では、データ モデルをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="4695f-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="4695f-127">詳細については、[タスク](http://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4695f-127">For more information, see [Tasks](http://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span></span>  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="4695f-128">新しいデータ モデルを使用してデータ サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="4695f-128">To create the data service by using the new data model</span></span>  
  
1.  <span data-ttu-id="4695f-129">データ モデルを表す .edmx ファイルを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="4695f-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>  
  
2.  <span data-ttu-id="4695f-130">**モデル ブラウザー**モデルを右クリックしをクリックして**プロパティ**、エンティティ コンテナーの名前をメモします。</span><span class="sxs-lookup"><span data-stu-id="4695f-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>  
  
3.  <span data-ttu-id="4695f-131">**ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトをクリックして**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="4695f-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
4.  <span data-ttu-id="4695f-132">**新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**です。</span><span class="sxs-lookup"><span data-stu-id="4695f-132">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
5.  <span data-ttu-id="4695f-133">サービスの名前を入力して、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="4695f-133">Supply a name for the service, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4695f-134">Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4695f-134">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="4695f-135">既定では、コード エディターのウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="4695f-135">By default, the code-editor window opens.</span></span>  
  
6.  <span data-ttu-id="4695f-136">データ サービスのコードで、データ サービスを定義するクラスの定義内のコメント `/* TODO: put your data source class name here */` を <xref:System.Data.Objects.ObjectContext> クラスから継承する型で置き換えます。この型はデータ モデルのエンティティ コンテナー (手順 2 で確認したコンテナー) です。</span><span class="sxs-lookup"><span data-stu-id="4695f-136">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>  
  
7.  <span data-ttu-id="4695f-137">データ サービスのコードで、承認されたクライアントがデータ サービスによって公開されているエンティティ セットにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="4695f-137">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="4695f-138">詳細については、次を参照してください。[データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="4695f-138">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
8.  <span data-ttu-id="4695f-139">Web ブラウザーを使用して Northwind.svc データ サービスをテストする、トピックの手順に従います[Web ブラウザーからサービスにアクセスする](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)です。</span><span class="sxs-lookup"><span data-stu-id="4695f-139">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4695f-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="4695f-140">See Also</span></span>  
 [<span data-ttu-id="4695f-141">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="4695f-141">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="4695f-142">Data Services プロバイダー</span><span class="sxs-lookup"><span data-stu-id="4695f-142">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="4695f-143">方法: リフレクション プロバイダーを使用してデータ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="4695f-143">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="4695f-144">方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="4695f-144">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
