---
title: "方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77a4b90b16a92e993d9283932b2a609f874c7568
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="85557-102">方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="85557-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="85557-103"> では、エンティティ データはデータ サービスとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="85557-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="85557-104">データ ソースがリレーショナル データベースの場合、このエンティティ データは [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="85557-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="85557-105">このトピックでは、既存のデータベースに基づき、このデータ モデルを使用して新しいデータ サービスを作成する [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Web アプリケーションで [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] ベースのデータ モデルを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85557-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web application that is based on an existing database and use this data model to create a new data service.</span></span>  
  
 <span data-ttu-id="85557-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] は、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロジェクトの外部に [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] モデルを生成できるコマンド ライン ツールも提供します。</span><span class="sxs-lookup"><span data-stu-id="85557-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project.</span></span> <span data-ttu-id="85557-107">詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルの生成に使用する EdmGen.exe](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)です。</span><span class="sxs-lookup"><span data-stu-id="85557-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="85557-108">既存のデータベースに基づく Entity Framework モデルを既存の Web アプリケーションに追加するには</span><span class="sxs-lookup"><span data-stu-id="85557-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>  
  
1.  <span data-ttu-id="85557-109">**プロジェクト** メニューのをクリックして**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="85557-109">On the **Project** menu, click **Add new item**.</span></span>  
  
2.  <span data-ttu-id="85557-110">**テンプレート** ウィンドウで、をクリックして、**データ**カテゴリ、および選択**ADO.NET エンティティ データ モデル**です。</span><span class="sxs-lookup"><span data-stu-id="85557-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="85557-111">モデルの名前を入力し、クリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="85557-111">Type the model name and then click **Add**.</span></span>  
  
     <span data-ttu-id="85557-112">[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ウィザードの最初のページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="85557-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>  
  
4.  <span data-ttu-id="85557-113">**モデルのコンテンツ**ダイアログ ボックスで、**データベースから生成**です。</span><span class="sxs-lookup"><span data-stu-id="85557-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="85557-114">その後、 **[次へ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85557-114">Then click **Next**.</span></span>  
  
5.  <span data-ttu-id="85557-115">クリックして、**新しい接続**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="85557-115">Click the **New Connection** button.</span></span>  
  
6.  <span data-ttu-id="85557-116">**接続プロパティ**ダイアログ ボックスで、サーバー名を入力、認証方法を選択して、データベース名を入力および順にクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="85557-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="85557-117">**データ接続の選択**データベース接続の設定 ダイアログ ボックスを更新します。</span><span class="sxs-lookup"><span data-stu-id="85557-117">The **Choose Your Data Connection**s dialog box is updated with your database connection settings.</span></span>  
  
7.  <span data-ttu-id="85557-118">いることを確認、**エンティティ接続設定を付けて App.Config に保存します。**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="85557-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="85557-119">その後、 **[次へ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85557-119">Then click **Next**.</span></span>  
  
8.  <span data-ttu-id="85557-120">**データベース オブジェクトの選択**ダイアログ ボックスで、すべてのデータベースのオブジェクトがデータ サービスの公開を計画することです。</span><span class="sxs-lookup"><span data-stu-id="85557-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85557-121">データ モデルに含まれるオブジェクトは、データ サービスによって自動的には公開されません。</span><span class="sxs-lookup"><span data-stu-id="85557-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="85557-122">これらのオブジェクトは、サービス自身によって明示的に公開される必要があります。</span><span class="sxs-lookup"><span data-stu-id="85557-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="85557-123">詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="85557-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
9. <span data-ttu-id="85557-124">をクリックして**完了**ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="85557-124">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="85557-125">特定のデータベースに基づく既定のデータ モデルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="85557-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="85557-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] では、データ モデルをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="85557-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="85557-127">詳細については、[タスク](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85557-127">For more information, see [Tasks](http://msdn.microsoft.com/en-us/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span></span>  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="85557-128">新しいデータ モデルを使用してデータ サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="85557-128">To create the data service by using the new data model</span></span>  
  
1.  <span data-ttu-id="85557-129">データ モデルを表す .edmx ファイルを [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で開きます。</span><span class="sxs-lookup"><span data-stu-id="85557-129">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], open the .edmx file that represents the data model.</span></span>  
  
2.  <span data-ttu-id="85557-130">**モデル ブラウザー**モデルを右クリックしをクリックして**プロパティ**、エンティティ コンテナーの名前をメモします。</span><span class="sxs-lookup"><span data-stu-id="85557-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>  
  
3.  <span data-ttu-id="85557-131">**ソリューション エクスプ ローラー**の名前を右クリックし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]プロジェクトをクリックして**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="85557-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
4.  <span data-ttu-id="85557-132">**新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**です。</span><span class="sxs-lookup"><span data-stu-id="85557-132">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
5.  <span data-ttu-id="85557-133">サービスの名前を入力して、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="85557-133">Supply a name for the service, and then click **OK**.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="85557-134"> で新しいサービスの XML マークアップおよびコード ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="85557-134"> creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="85557-135">既定では、コード エディターのウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="85557-135">By default, the code-editor window opens.</span></span>  
  
6.  <span data-ttu-id="85557-136">データ サービスのコードで、データ サービスを定義するクラスの定義内のコメント `/* TODO: put your data source class name here */` を <xref:System.Data.Objects.ObjectContext> クラスから継承する型で置き換えます。この型はデータ モデルのエンティティ コンテナー (手順 2 で確認したコンテナー) です。</span><span class="sxs-lookup"><span data-stu-id="85557-136">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>  
  
7.  <span data-ttu-id="85557-137">データ サービスのコードで、承認されたクライアントがデータ サービスによって公開されているエンティティ セットにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="85557-137">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="85557-138">詳細については、次を参照してください。[データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="85557-138">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
8.  <span data-ttu-id="85557-139">Web ブラウザーを使用して Northwind.svc データ サービスをテストする、トピックの手順に従います[Web ブラウザーからサービスにアクセスする](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)です。</span><span class="sxs-lookup"><span data-stu-id="85557-139">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85557-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="85557-140">See Also</span></span>  
 [<span data-ttu-id="85557-141">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="85557-141">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="85557-142">データ サービス プロバイダー</span><span class="sxs-lookup"><span data-stu-id="85557-142">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="85557-143">方法: リフレクション プロバイダーを使用してデータ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="85557-143">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="85557-144">方法: SQL データ ソースを LINQ を使用してデータ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="85557-144">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
