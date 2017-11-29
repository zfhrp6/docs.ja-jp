---
title: "方法 : LINQ を使用してクエリ結果をフィルター処理する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09f2eb65858853fd759ae033f749151b348c124d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="8d610-102">方法 : LINQ を使用してクエリ結果をフィルター処理する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d610-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="8d610-103">統合言語クエリ (LINQ) では、簡単にデータベース情報にアクセスしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="8d610-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="8d610-104">次の例は、SQL Server データベースに対してクエリを実行し、特定の値によって結果をフィルター処理を使用して、新しいアプリケーションを作成する方法を示します、`Where`句。</span><span class="sxs-lookup"><span data-stu-id="8d610-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="8d610-105">詳細については、次を参照してください。 [Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="8d610-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="8d610-106">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d610-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="8d610-107">開発用コンピューター上に Northwind サンプル データベースがないことからダウンロードする、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="8d610-107">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="8d610-108">手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)です。</span><span class="sxs-lookup"><span data-stu-id="8d610-108">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="8d610-109">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="8d610-109">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="8d610-110">Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="8d610-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="8d610-111">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**です。</span><span class="sxs-lookup"><span data-stu-id="8d610-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="8d610-112">Northwind サンプル データベースへの接続を有効なを指定します。</span><span class="sxs-lookup"><span data-stu-id="8d610-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="8d610-113">LINQ to SQL ファイルを含むプロジェクトを追加するのには</span><span class="sxs-lookup"><span data-stu-id="8d610-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="8d610-114">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d610-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="8d610-115">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="8d610-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="8d610-116">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d610-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="8d610-117">選択、 **LINQ to SQL クラス**項目テンプレート。</span><span class="sxs-lookup"><span data-stu-id="8d610-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="8d610-118">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="8d610-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="8d610-119">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d610-119">Click **Add**.</span></span> <span data-ttu-id="8d610-120">オブジェクト リレーショナル デザイナー (O/R デザイナー) は、northwind.dbml ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="8d610-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="8d610-121">O/R デザイナーをクエリにテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="8d610-121">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="8d610-122">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="8d610-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="8d610-123">展開して、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="8d610-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="8d610-124">O/R デザイナーが閉じられたかと、以前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="8d610-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="8d610-125">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8d610-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="8d610-126">Orders テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="8d610-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="8d610-127">デザイナーを新規作成`Customer`と`Order`プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8d610-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="8d610-128">デザイナーが自動的にテーブル間のリレーションシップを検出し、関連オブジェクトのプロパティの子を作成することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8d610-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="8d610-129">たとえば、IntelliSense ことが表示されます、`Customer`オブジェクトには、`Orders`その顧客に関連するすべての注文のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8d610-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="8d610-130">変更を保存し、デザイナーを終了します。</span><span class="sxs-lookup"><span data-stu-id="8d610-130">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="8d610-131">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="8d610-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="8d610-132">データベースを照会し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="8d610-132">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="8d610-133">**ツールボックス**、ドラッグ、 <xref:System.Windows.Forms.DataGridView> Form1、プロジェクトの既定の Windows フォームにコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="8d610-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="8d610-134">コードを追加する Form1 をダブルクリックして、`Load`フォームのイベントです。</span><span class="sxs-lookup"><span data-stu-id="8d610-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="8d610-135">O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8d610-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="8d610-136">このオブジェクトには、個々 のオブジェクトと各テーブルのコレクションだけでなく、それらのテーブルへのアクセスに必要なコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8d610-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="8d610-137"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="8d610-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="8d610-138">このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。</span><span class="sxs-lookup"><span data-stu-id="8d610-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="8d610-139">インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーで指定されたテーブル内のコードとクエリ。</span><span class="sxs-lookup"><span data-stu-id="8d610-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="8d610-140">次のコードを追加、`Load`データ コンテキストのプロパティとして公開されているテーブルを照会するイベントです。</span><span class="sxs-lookup"><span data-stu-id="8d610-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="8d610-141">クエリの結果をフィルター処理およびに配置されている顧客だけを返します`London`です。</span><span class="sxs-lookup"><span data-stu-id="8d610-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="8d610-142">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="8d610-142">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="8d610-143">試用できるその他の一部のフィルターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8d610-143">Following are some other filters that you can try.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8d610-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d610-144">See Also</span></span>  
 [<span data-ttu-id="8d610-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="8d610-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="8d610-146">クエリ</span><span class="sxs-lookup"><span data-stu-id="8d610-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="8d610-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8d610-147">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
 [<span data-ttu-id="8d610-148">DataContext メソッド (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="8d610-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
