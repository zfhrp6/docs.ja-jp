---
title: "方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する (WCF Data Services)"
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
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52529689242342afa8920a7b01b532a24337f562
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="29cdc-102">方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="29cdc-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="29cdc-103"> では、エンティティ データはデータ サービスとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="29cdc-104">リフレクション プロバイダーを使用すると、メンバーを公開する任意のクラスに基づいているデータ モデルの定義を返す、<xref:System.Linq.IQueryable%601>実装します。</span><span class="sxs-lookup"><span data-stu-id="29cdc-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="29cdc-105">データ ソース内のデータに更新を加えるには、これらのクラスも <xref:System.Data.Services.IUpdatable> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29cdc-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="29cdc-106">詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="29cdc-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="29cdc-107">このトピックでは、リフレクション プロバイダーを使用して Northwind サンプル データベースにアクセスする LINQ to SQL クラスを作成する方法と、これらのデータ クラスに基づくデータ サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="29cdc-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="29cdc-108">LINQ to SQL クラスをプロジェクトに追加するには</span><span class="sxs-lookup"><span data-stu-id="29cdc-108">To add LINQ to SQL classes to a project</span></span>  
  
1.  <span data-ttu-id="29cdc-109">Visual Basic または c# のアプリケーション内での**プロジェクト** メニューのをクリックして**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="29cdc-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="29cdc-110">クリックして、 **LINQ to SQL クラス**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="29cdc-110">Click the **LINQ to SQL Classes** template.</span></span>  
  
3.  <span data-ttu-id="29cdc-111">名前を変更**Northwind.dbml**です。</span><span class="sxs-lookup"><span data-stu-id="29cdc-111">Change the name to **Northwind.dbml**.</span></span>  
  
4.  <span data-ttu-id="29cdc-112">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="29cdc-112">Click **Add**.</span></span>  
  
     <span data-ttu-id="29cdc-113">Northwind.dbml ファイルがプロジェクトに追加され、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開きます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>  
  
5.  <span data-ttu-id="29cdc-114">**サーバー**/**データベース エクスプ ローラー**、Northwind の下にある展開**テーブル**をドラッグし、`Customers`テーブルをオブジェクト リレーショナル デザイナー (O/Rデザイナーの場合)。</span><span class="sxs-lookup"><span data-stu-id="29cdc-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>  
  
     <span data-ttu-id="29cdc-115">`Customer` エンティティ クラスが作成され、デザイン サーフェイスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-115">A `Customer` entity class is created and appears on the design surface.</span></span>  
  
6.  <span data-ttu-id="29cdc-116">`Orders` テーブル、`Order_Details` テーブル、および `Products` テーブルに対して手順 6 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="29cdc-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>  
  
7.  <span data-ttu-id="29cdc-117">LINQ to SQL クラスとクリックを表す新しい .dbml ファイルを右クリックして**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="29cdc-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>  
  
     <span data-ttu-id="29cdc-118"><xref:System.Data.Linq.DataContext> クラス (この場合は `NorthwindDataContext`) から継承するクラスの部分クラス定義を含む Northwind.cs という新しい分離コード ページが作成されます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>  
  
8.  <span data-ttu-id="29cdc-119">Northwind.cs コード ファイルの内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="29cdc-120">このコードでは、<xref:System.Data.Linq.DataContext> と、および LINQ to SQL によって生成されたデータ クラスを拡張して、リフレクション プロバイダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="29cdc-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="29cdc-121">LINQ to SQL ベースのデータ モデルを使用してデータ サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="29cdc-121">To create a data service by using a LINQ to SQL-based data model</span></span>  
  
1.  <span data-ttu-id="29cdc-122">**ソリューション エクスプ ローラー**、ASP.NET プロジェクトの名前を右クリックし、クリックして**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="29cdc-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="29cdc-123">**新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**です。</span><span class="sxs-lookup"><span data-stu-id="29cdc-123">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="29cdc-124">サービスの名前を入力して、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="29cdc-124">Supply a name for the service, and then click **OK**.</span></span>  
  
     <span data-ttu-id="29cdc-125">Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-125">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="29cdc-126">既定では、コード エディターのウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-126">By default, the code-editor window opens.</span></span>  
  
4.  <span data-ttu-id="29cdc-127">データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindDataContext`) で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-127">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>  
  
5.  <span data-ttu-id="29cdc-128">データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-128">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     <span data-ttu-id="29cdc-129">指定した 3 つのエンティティ セットのリソースへのクライアント アクセスが承認されます。</span><span class="sxs-lookup"><span data-stu-id="29cdc-129">This enables authorized clients to access resources for the three specified entity sets.</span></span>  
  
6.  <span data-ttu-id="29cdc-130">Web ブラウザーを使用して Northwind.svc データ サービスをテストする、トピックの手順に従います[Web ブラウザーからサービスにアクセスする](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)です。</span><span class="sxs-lookup"><span data-stu-id="29cdc-130">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29cdc-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="29cdc-131">See Also</span></span>  
 [<span data-ttu-id="29cdc-132">方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="29cdc-132">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [<span data-ttu-id="29cdc-133">方法: リフレクション プロバイダーを使用してデータ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="29cdc-133">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="29cdc-134">データ サービス プロバイダー</span><span class="sxs-lookup"><span data-stu-id="29cdc-134">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
