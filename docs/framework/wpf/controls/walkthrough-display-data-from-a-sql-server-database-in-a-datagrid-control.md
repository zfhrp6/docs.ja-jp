---
title: "チュートリアル: DataGrid コントロールで SQL Server データベースのデータを表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0397206a05ef47a7fc9b130fbd13fa19a0d766fa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="920bd-102">チュートリアル: DataGrid コントロールで SQL Server データベースのデータを表示する</span><span class="sxs-lookup"><span data-stu-id="920bd-102">Walkthrough: Display Data from a SQL Server Database in a DataGrid Control</span></span>
<span data-ttu-id="920bd-103">このチュートリアルで、SQL Server データベースからデータを取得およびそのデータを表示、<xref:System.Windows.Controls.DataGrid>コントロール。</span><span class="sxs-lookup"><span data-stu-id="920bd-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="920bd-104">LINQ を使用して、エンティティ クラスから指定されたデータを取得するクエリを記述するのにと、データを表すエンティティ クラスを作成するのにには、ADO.NET Entity Framework を使用します。</span><span class="sxs-lookup"><span data-stu-id="920bd-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="920bd-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="920bd-105">Prerequisites</span></span>  
 <span data-ttu-id="920bd-106">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="920bd-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="920bd-107">。</span><span class="sxs-lookup"><span data-stu-id="920bd-107">.</span></span>  
  
-   <span data-ttu-id="920bd-108">SQL Server または SQL Server Express が付属している、AdventureWorks サンプル データベースがあるの実行中のインスタンスへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="920bd-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="920bd-109">AdventureWorks データベースをダウンロードすることができます、 [GitHub](https://github.com/Microsoft/sql-server-samples/releases)です。</span><span class="sxs-lookup"><span data-stu-id="920bd-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>  
  
### <a name="to-create-entity-classes"></a><span data-ttu-id="920bd-110">エンティティ クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="920bd-110">To create entity classes</span></span>  
  
1.  <span data-ttu-id="920bd-111">Visual Basic または C# の場合で新しい WPF アプリケーション プロジェクトを作成し、名前`DataGridSQLExample`です。</span><span class="sxs-lookup"><span data-stu-id="920bd-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>  
  
2.  <span data-ttu-id="920bd-112">ソリューション エクスプ ローラーでプロジェクトを右クリックし、**追加**、し、**新しい項目の**します。</span><span class="sxs-lookup"><span data-stu-id="920bd-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>  
  
     <span data-ttu-id="920bd-113">[新しい項目の追加] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="920bd-113">The Add New Item dialog box appears.</span></span>  
  
3.  <span data-ttu-id="920bd-114">インストールされたテンプレート ペインで選択**データ**、テンプレートの一覧で選択および**ADO.NET エンティティ データ モデル**l です。</span><span class="sxs-lookup"><span data-stu-id="920bd-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Mode**l.</span></span>  
  
     <span data-ttu-id="920bd-115">![ADO.NET エンティティ データ モデルを選択して](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span><span class="sxs-lookup"><span data-stu-id="920bd-115">![Select ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span></span>  
  
4.  <span data-ttu-id="920bd-116">ファイルの名前を付けます`AdventureWorksModel.edmx` をクリックし、**追加**です。</span><span class="sxs-lookup"><span data-stu-id="920bd-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>  
  
     <span data-ttu-id="920bd-117">Entity Data Model ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="920bd-117">The Entity Data Model Wizard appears.</span></span>  
  
5.  <span data-ttu-id="920bd-118">モデルのコンテンツの選択 画面で、次のように選択します。**データベースから生成** をクリックし、**次**です。</span><span class="sxs-lookup"><span data-stu-id="920bd-118">In the Choose Model Contents screen, select **Generate from database** and then click **Next**.</span></span>  
  
     <span data-ttu-id="920bd-119">![データベース オプションから生成 を選択](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span><span class="sxs-lookup"><span data-stu-id="920bd-119">![Select Generate from database option](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span></span>  
  
6.  <span data-ttu-id="920bd-120">データ接続の選択 画面で、AdventureWorksLT2008 データベースへの接続を提供します。</span><span class="sxs-lookup"><span data-stu-id="920bd-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="920bd-121">詳細については、次を参照してください。[を選択して、データ接続 ダイアログ ボックス](http://go.microsoft.com/fwlink/?LinkId=160190)です。</span><span class="sxs-lookup"><span data-stu-id="920bd-121">For more information, see [Choose Your Data Connection Dialog Box](http://go.microsoft.com/fwlink/?LinkId=160190).</span></span>  
  
     <span data-ttu-id="920bd-122">![データベースへの接続を提供](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span><span class="sxs-lookup"><span data-stu-id="920bd-122">![Provide connection to database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span></span>  
  
7.  <span data-ttu-id="920bd-123">名があるかどうかを確認`AdventureWorksLT2008Entities`ことと、**エンティティ接続設定を付けて App.Config に保存** チェック ボックスを選択して、をクリックして**次**です。</span><span class="sxs-lookup"><span data-stu-id="920bd-123">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="920bd-124">データベース オブジェクトの選択 画面で、テーブル ノードを展開し、選択、**製品**と**ProductCategory**テーブル。</span><span class="sxs-lookup"><span data-stu-id="920bd-124">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>  
  
     <span data-ttu-id="920bd-125">テーブルのすべてのエンティティ クラスを生成することができます。ただし、この例でのみデータを取得する 2 つのテーブルからです。</span><span class="sxs-lookup"><span data-stu-id="920bd-125">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>  
  
     <span data-ttu-id="920bd-126">![テーブルからの Product および ProductCategory の選択](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="920bd-126">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>  
  
9. <span data-ttu-id="920bd-127">**[完了]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="920bd-127">Click **Finish**.</span></span>  
  
     <span data-ttu-id="920bd-128">エンティティ デザイナーで、Product および ProductCategory エンティティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="920bd-128">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>  
  
     <span data-ttu-id="920bd-129">![Product および ProductCategory エンティティ モデル](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="920bd-129">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>  
  
### <a name="to-retrieve-and-present-the-data"></a><span data-ttu-id="920bd-130">取得して、データの表示</span><span class="sxs-lookup"><span data-stu-id="920bd-130">To retrieve and present the data</span></span>  
  
1.  <span data-ttu-id="920bd-131">MainWindow.xaml ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="920bd-131">Open the MainWindow.xaml file.</span></span>  
  
2.  <span data-ttu-id="920bd-132">設定、<xref:System.Windows.FrameworkElement.Width%2A>プロパティを<xref:System.Windows.Window>450 にします。</span><span class="sxs-lookup"><span data-stu-id="920bd-132">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>  
  
3.  <span data-ttu-id="920bd-133">XAML エディターで、次のコードを追加<xref:System.Windows.Controls.DataGrid>タグの間、`<Grid>`と`</Grid>`タグを追加する、<xref:System.Windows.Controls.DataGrid>という`dataGrid1`です。</span><span class="sxs-lookup"><span data-stu-id="920bd-133">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     <span data-ttu-id="920bd-134">![DataGrid のあるウィンドウ](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="920bd-134">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>  
  
4.  <span data-ttu-id="920bd-135"><xref:System.Windows.Window> を選択します。</span><span class="sxs-lookup"><span data-stu-id="920bd-135">Select the <xref:System.Windows.Window>.</span></span>  
  
5.  <span data-ttu-id="920bd-136">イベント ハンドラーを作成する [プロパティ] ウィンドウまたは XAML エディターを使用して、<xref:System.Windows.Window>という`Window_Loaded`の<xref:System.Windows.FrameworkElement.Loaded>イベント。</span><span class="sxs-lookup"><span data-stu-id="920bd-136">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="920bd-137">詳細については、次を参照してください。[する方法: 単純なイベント ハンドラーを作成する](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480)です。</span><span class="sxs-lookup"><span data-stu-id="920bd-137">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>  
  
     <span data-ttu-id="920bd-138">次は、MainWindow.xaml の XAML を示します。</span><span class="sxs-lookup"><span data-stu-id="920bd-138">The following shows the XAML for MainWindow.xaml.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="920bd-139">Visual Basic で MainWindow.xaml の最初の行を使用している場合は置き換えます`x:Class="DataGridSQLExample.MainWindow"`で`x:Class="MainWindow"`です。</span><span class="sxs-lookup"><span data-stu-id="920bd-139">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  <span data-ttu-id="920bd-140">分離コード ファイル (MainWindow.xaml.vb または MainWindow.xaml.cs) を開き、<xref:System.Windows.Window>です。</span><span class="sxs-lookup"><span data-stu-id="920bd-140">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>  
  
7.  <span data-ttu-id="920bd-141">結合されたテーブルから特定の値を取得および設定するには、次のコードを追加、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.DataGrid>クエリの結果にします。</span><span class="sxs-lookup"><span data-stu-id="920bd-141">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  <span data-ttu-id="920bd-142">例を実行します。</span><span class="sxs-lookup"><span data-stu-id="920bd-142">Run the example.</span></span>  
  
     <span data-ttu-id="920bd-143">参照する必要があります、<xref:System.Windows.Controls.DataGrid>データを表示します。</span><span class="sxs-lookup"><span data-stu-id="920bd-143">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>  
  
     <span data-ttu-id="920bd-144">![SQL データベースからデータがある DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="920bd-144">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="920bd-145">次の手順</span><span class="sxs-lookup"><span data-stu-id="920bd-145">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="920bd-146">参照</span><span class="sxs-lookup"><span data-stu-id="920bd-146">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="920bd-147">方法は i: どこから始めたら WPF アプリケーションで Entity Framework としますか。</span><span class="sxs-lookup"><span data-stu-id="920bd-147">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](http://go.microsoft.com/fwlink/?LinkId=159868)
