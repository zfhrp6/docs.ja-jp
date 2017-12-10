---
title: "方法 : LINQ を使用したデータの数、合計、または平均の算出 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a8c77804a9813d6127edcf4bd8371e0de2b36074
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="64147-102">方法 : LINQ を使用したデータの数、合計、または平均の算出 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64147-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="64147-103">統合言語クエリ (LINQ) では、簡単にデータベース情報にアクセスしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="64147-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="64147-104">次の例では、SQL Server データベースに対してクエリを実行する新しいアプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="64147-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="64147-105">サンプルは、カウントの合計を計算しを使用して、結果の平均を計算、`Aggregate`と`Group By`句。</span><span class="sxs-lookup"><span data-stu-id="64147-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="64147-106">詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="64147-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="64147-107">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="64147-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="64147-108">開発用コンピューター上に Northwind サンプル データベースがないことからダウンロードする、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="64147-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="64147-109">手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。</span><span class="sxs-lookup"><span data-stu-id="64147-109">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="64147-110">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="64147-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="64147-111">Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="64147-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="64147-112">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**です。</span><span class="sxs-lookup"><span data-stu-id="64147-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="64147-113">Northwind サンプル データベースへの接続を有効なを指定します。</span><span class="sxs-lookup"><span data-stu-id="64147-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="64147-114">LINQ to SQL ファイルを含むプロジェクトを追加するのには</span><span class="sxs-lookup"><span data-stu-id="64147-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="64147-115">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64147-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="64147-116">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="64147-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="64147-117">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64147-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="64147-118">選択、 **LINQ to SQL クラス**項目テンプレート。</span><span class="sxs-lookup"><span data-stu-id="64147-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="64147-119">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="64147-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="64147-120">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="64147-120">Click **Add**.</span></span> <span data-ttu-id="64147-121">Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。</span><span class="sxs-lookup"><span data-stu-id="64147-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="64147-122">O/R デザイナーをクエリにテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="64147-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="64147-123">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="64147-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="64147-124">展開して、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="64147-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="64147-125">O/R デザイナーが閉じられたかと、以前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="64147-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="64147-126">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="64147-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="64147-127">Orders テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="64147-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="64147-128">デザイナーを新規作成`Customer`と`Order`プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="64147-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="64147-129">デザイナーが自動的にテーブル間のリレーションシップを検出し、関連オブジェクトのプロパティの子を作成することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="64147-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="64147-130">たとえば、IntelliSense ことが表示されます、`Customer`オブジェクトには、`Orders`その顧客に関連するすべての注文のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="64147-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="64147-131">変更を保存し、デザイナーを終了します。</span><span class="sxs-lookup"><span data-stu-id="64147-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="64147-132">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="64147-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="64147-133">データベースを照会し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="64147-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="64147-134">**ツールボックス**、ドラッグ、 <xref:System.Windows.Forms.DataGridView> Form1、プロジェクトの既定の Windows フォームにコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="64147-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="64147-135">コードを追加する Form1 をダブルクリックして、`Load`フォームのイベントです。</span><span class="sxs-lookup"><span data-stu-id="64147-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="64147-136">O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="64147-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="64147-137">このオブジェクトには、これらのテーブルにアクセスして、個々 のオブジェクトと各テーブルのコレクションにアクセスする必要があります、コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="64147-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="64147-138"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="64147-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="64147-139">このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。</span><span class="sxs-lookup"><span data-stu-id="64147-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="64147-140">インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーで指定されたテーブル内のコードとクエリ。</span><span class="sxs-lookup"><span data-stu-id="64147-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="64147-141">次のコードを追加、`Load`イベントのプロパティとして公開されているテーブルに対するクエリを<xref:System.Data.Linq.DataContext>とカウント、合計、および結果を平均します。</span><span class="sxs-lookup"><span data-stu-id="64147-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="64147-142">サンプルを使用、`Aggregate`句を 1 つの結果のクエリと`Group By`の平均値を表示する句の結果をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="64147-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="64147-143">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="64147-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64147-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="64147-144">See Also</span></span>  
 [<span data-ttu-id="64147-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="64147-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="64147-146">クエリ</span><span class="sxs-lookup"><span data-stu-id="64147-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="64147-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="64147-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="64147-148">DataContext メソッド (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="64147-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="64147-149">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="64147-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="64147-150">Group By 句</span><span class="sxs-lookup"><span data-stu-id="64147-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
