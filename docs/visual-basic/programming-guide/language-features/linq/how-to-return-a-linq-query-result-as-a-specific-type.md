---
title: "方法 : LINQ クエリ結果を特定の型で返す (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4f206310be9fb00606ff351722eb1cf491b1c693
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="33e6a-102">方法 : LINQ クエリ結果を特定の型で返す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33e6a-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="33e6a-103">統合言語クエリ (LINQ) では、簡単にデータベース情報にアクセスしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="33e6a-104">既定では、LINQ クエリは、匿名型としてオブジェクトの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="33e6a-105">クエリを使用して、特定の種類の一覧を返すことを指定することも、`Select`句。</span><span class="sxs-lookup"><span data-stu-id="33e6a-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="33e6a-106">次の例では、SQL Server データベースに対してクエリを実行し、特定の名前付きの型として、結果を射影する新しいアプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="33e6a-107">詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)と[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="33e6a-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="33e6a-108">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="33e6a-109">開発用コンピューター上に Northwind サンプル データベースがないことからダウンロードする、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="33e6a-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="33e6a-110">手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)です。</span><span class="sxs-lookup"><span data-stu-id="33e6a-110">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="33e6a-111">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="33e6a-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="33e6a-112">Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="33e6a-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="33e6a-113">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**です。</span><span class="sxs-lookup"><span data-stu-id="33e6a-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="33e6a-114">Northwind サンプル データベースへの接続を有効なを指定します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="33e6a-115">LINQ to SQL ファイルを含むプロジェクトを追加するのには</span><span class="sxs-lookup"><span data-stu-id="33e6a-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="33e6a-116">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33e6a-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="33e6a-117">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="33e6a-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="33e6a-118">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33e6a-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="33e6a-119">選択、 **LINQ to SQL クラス**項目テンプレート。</span><span class="sxs-lookup"><span data-stu-id="33e6a-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="33e6a-120">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="33e6a-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="33e6a-121">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33e6a-121">Click **Add**.</span></span> <span data-ttu-id="33e6a-122">Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。</span><span class="sxs-lookup"><span data-stu-id="33e6a-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="33e6a-123">O/R デザイナーをクエリにテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="33e6a-123">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="33e6a-124">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="33e6a-125">展開して、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="33e6a-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="33e6a-126">O/R デザイナーが閉じられたかと、以前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="33e6a-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="33e6a-127">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="33e6a-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="33e6a-128">デザイナーが新たに作成`Customer`プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="33e6a-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="33e6a-129">クエリの結果を射影することができます、`Customer`型または作成した型として。</span><span class="sxs-lookup"><span data-stu-id="33e6a-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="33e6a-130">このサンプルでは、後の手順で新しい型が作成され、クエリの結果がその型をプロジェクトすることがします。</span><span class="sxs-lookup"><span data-stu-id="33e6a-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3.  <span data-ttu-id="33e6a-131">変更を保存し、デザイナーを終了します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="33e6a-132">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="33e6a-133">データベースを照会し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="33e6a-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="33e6a-134">**ツールボックス**、ドラッグ、 <xref:System.Windows.Forms.DataGridView> Form1、プロジェクトの既定の Windows フォームにコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="33e6a-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="33e6a-135">Form1 クラスを変更する Form1 をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="33e6a-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3.  <span data-ttu-id="33e6a-136">後に、 `End Class` Form1 クラスのステートメントを作成する次のコードを追加する、`CustomerInfo`このサンプルのクエリの結果を保持する型。</span><span class="sxs-lookup"><span data-stu-id="33e6a-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  <span data-ttu-id="33e6a-137">O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>をプロジェクトにオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="33e6a-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="33e6a-138">このオブジェクトには、これらのテーブルにアクセスして、個々 のオブジェクトと各テーブルのコレクションにアクセスする必要があります、コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="33e6a-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="33e6a-139"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="33e6a-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="33e6a-140">このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="33e6a-141">インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーで指定されたテーブル内のコードとクエリ。</span><span class="sxs-lookup"><span data-stu-id="33e6a-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="33e6a-142">`Load` Form1 クラスのイベントは、データ コンテキストのプロパティとして公開されているテーブルを照会する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="33e6a-143">`Select`新しいクエリの句が作成されます`CustomerInfo`クエリ結果の項目ごとに、匿名型ではなく型です。</span><span class="sxs-lookup"><span data-stu-id="33e6a-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  <span data-ttu-id="33e6a-144">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="33e6a-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e6a-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="33e6a-145">See Also</span></span>  
 [<span data-ttu-id="33e6a-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="33e6a-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="33e6a-147">クエリ</span><span class="sxs-lookup"><span data-stu-id="33e6a-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="33e6a-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="33e6a-148">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
 [<span data-ttu-id="33e6a-149">DataContext メソッド (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="33e6a-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
