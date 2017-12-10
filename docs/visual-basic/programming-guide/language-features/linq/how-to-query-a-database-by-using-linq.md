---
title: "方法 : LINQ を使用してデータベースを照会する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e59c440e5553366d27fed6e5c53c5c463172906b
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="acbc8-102">方法 : LINQ を使用してデータベースを照会する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acbc8-102">How to: Query a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="acbc8-103">統合言語クエリ (LINQ) では、簡単にデータベース情報にアクセスしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="acbc8-104">次の例では、SQL Server データベースに対してクエリを実行する新しいアプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span>  
  
 <span data-ttu-id="acbc8-105">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="acbc8-106">開発用コンピューター上に Northwind サンプル データベースがないことからダウンロードする、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="acbc8-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="acbc8-107">手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。</span><span class="sxs-lookup"><span data-stu-id="acbc8-107">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="acbc8-108">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="acbc8-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="acbc8-109">Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="acbc8-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="acbc8-110">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**です。</span><span class="sxs-lookup"><span data-stu-id="acbc8-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="acbc8-111">Northwind サンプル データベースへの接続を有効なを指定します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="acbc8-112">LINQ to SQL ファイルを含むプロジェクトを追加するのには</span><span class="sxs-lookup"><span data-stu-id="acbc8-112">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="acbc8-113">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acbc8-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="acbc8-114">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="acbc8-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="acbc8-115">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acbc8-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="acbc8-116">選択、 **LINQ to SQL クラス**項目テンプレート。</span><span class="sxs-lookup"><span data-stu-id="acbc8-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="acbc8-117">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="acbc8-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="acbc8-118">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="acbc8-118">Click **Add**.</span></span> <span data-ttu-id="acbc8-119">Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。</span><span class="sxs-lookup"><span data-stu-id="acbc8-119">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="acbc8-120">O/R デザイナーをクエリにテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="acbc8-120">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="acbc8-121">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="acbc8-122">展開して、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="acbc8-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="acbc8-123">O/R デザイナーが閉じられたかと、以前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="acbc8-123">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="acbc8-124">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acbc8-124">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="acbc8-125">Orders テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="acbc8-125">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="acbc8-126">デザイナーを新規作成`Customer`と`Order`プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="acbc8-126">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="acbc8-127">デザイナーが自動的にテーブル間のリレーションシップを検出し、関連オブジェクトのプロパティの子を作成することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="acbc8-127">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="acbc8-128">たとえば、IntelliSense ことが表示されます、`Customer`オブジェクトには、`Orders`その顧客に関連するすべての注文のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="acbc8-128">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="acbc8-129">変更を保存し、デザイナーを終了します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="acbc8-130">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-130">Save your project.</span></span>  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="acbc8-131">データベースを照会し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="acbc8-131">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="acbc8-132">**ツールボックス**、ドラッグ、 <xref:System.Windows.Forms.DataGridView> Form1、プロジェクトの既定の Windows フォームにコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="acbc8-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="acbc8-133">コードを追加する Form1 をダブルクリックして、`Load`フォームのイベントです。</span><span class="sxs-lookup"><span data-stu-id="acbc8-133">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="acbc8-134">O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="acbc8-134">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="acbc8-135">このオブジェクトには、個々 のオブジェクトと各テーブルのコレクションだけでなく、それらのテーブルへのアクセスに必要なコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="acbc8-135">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="acbc8-136"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="acbc8-136">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="acbc8-137">このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="acbc8-138">インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーで指定されたテーブル内のコードとクエリ。</span><span class="sxs-lookup"><span data-stu-id="acbc8-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="acbc8-139">次のコードを追加、`Load`データ コンテキストのプロパティとして公開されているテーブルを照会するイベントです。</span><span class="sxs-lookup"><span data-stu-id="acbc8-139">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="acbc8-140">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-140">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="acbc8-141">試用できるいくつかの追加のクエリを次に示します。</span><span class="sxs-lookup"><span data-stu-id="acbc8-141">Following are some additional queries that you can try:</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]  
    [!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="acbc8-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="acbc8-142">See Also</span></span>  
 [<span data-ttu-id="acbc8-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="acbc8-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="acbc8-144">クエリ</span><span class="sxs-lookup"><span data-stu-id="acbc8-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="acbc8-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="acbc8-145">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="acbc8-146">DataContext メソッド (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="acbc8-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
