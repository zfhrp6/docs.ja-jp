---
title: "方法: LINQ (Visual Basic) を使用してクエリ結果内の最小値と最大値を検索 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 76f5ad02dc79bf8447ae0656c0ea90b5d9bb8edc
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="ded7b-102">方法 : LINQ を使用したクエリ結果内の最小値と最大値の検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ded7b-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="ded7b-103">統合言語クエリ (LINQ) により、簡単にデータベース情報にアクセスし、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="ded7b-104">次の例では、SQL Server データベースに対してクエリを実行する新しいアプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="ded7b-105">このサンプルを使用して結果を得るのための最小値と最大値を決定する、`Aggregate`と`Group By`句。</span><span class="sxs-lookup"><span data-stu-id="ded7b-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="ded7b-106">詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="ded7b-107">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="ded7b-108">開発用コンピューターに Northwind サンプル データベースがないをからダウンロードできます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="ded7b-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="ded7b-109">手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="ded7b-110">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="ded7b-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="ded7b-111">Visual Studio で開きます**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="ded7b-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="ded7b-112">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="ded7b-113">Northwind サンプル データベースに有効な接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="ded7b-114">LINQ to SQL ファイルを含むプロジェクトを追加するのには</span><span class="sxs-lookup"><span data-stu-id="ded7b-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="ded7b-115">Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="ded7b-116">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="ded7b-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="ded7b-117">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ded7b-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="ded7b-118">選択、 **LINQ to SQL クラス**項目テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="ded7b-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="ded7b-119">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="ded7b-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="ded7b-120">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ded7b-120">Click **Add**.</span></span> <span data-ttu-id="ded7b-121">Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。</span><span class="sxs-lookup"><span data-stu-id="ded7b-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="ded7b-122">O/R デザイナーをクエリにテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="ded7b-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="ded7b-123">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="ded7b-124">展開、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="ded7b-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="ded7b-125">O/R デザイナーを閉じていた場合は、前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="ded7b-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="ded7b-126">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ded7b-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="ded7b-127">Orders テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ded7b-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="ded7b-128">デザイナーを新規作成`Customer`と`Order`プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ded7b-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="ded7b-129">デザイナーが自動的にテーブル間のリレーションシップを検出し、関連オブジェクトのプロパティの子を作成することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ded7b-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="ded7b-130">たとえば、IntelliSense が表示されますが、`Customer`オブジェクトには、`Orders`その顧客に関連するすべての発注書のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="ded7b-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="ded7b-131">変更内容を保存してデザイナーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ded7b-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="ded7b-132">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="ded7b-133">データベースを照会し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="ded7b-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="ded7b-134">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>コントロールをプロジェクトの Form1 の既定の Windows フォームにします</xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="ded7b-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="ded7b-135">コードを追加する Form1 をダブルクリックして、`Load`形式のイベントです。</span><span class="sxs-lookup"><span data-stu-id="ded7b-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="ded7b-136">O/R デザイナーにテーブルを追加したときに、デザイナーが追加、 <xref:System.Data.Linq.DataContext>、プロジェクトのオブジェクト</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="ded7b-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="ded7b-137">このオブジェクトには、個々 のオブジェクトと各テーブルのコレクションだけでなく、それらのテーブルにアクセスするために必要なコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ded7b-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="ded7b-138"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいての .dbml ファイルの名前</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="ded7b-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="ded7b-139">このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="ded7b-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="ded7b-140">インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext>O/R デザイナーで指定されたテーブル内のコードとクエリ</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="ded7b-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="ded7b-141">次のコードを追加、`Load`イベントです。</span><span class="sxs-lookup"><span data-stu-id="ded7b-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="ded7b-142">このコードは、データ コンテキストのプロパティとして公開され、結果を得るのための最小値と最大値を決定するテーブルを照会します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="ded7b-143">サンプルでは、彼は使用`Aggregate`、単一の結果のクエリに句と`Group By`の平均値を表示する句の結果をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     <span data-ttu-id="ded7b-144">[!code-vb[VbLINQToSQLHowTos&#14;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ded7b-144">[!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]</span></span>  
  
4.  <span data-ttu-id="ded7b-145">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="ded7b-145">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded7b-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="ded7b-146">See Also</span></span>  
 <span data-ttu-id="ded7b-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="ded7b-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="ded7b-148"> [クエリ](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="ded7b-148"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="ded7b-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="ded7b-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="ded7b-150"> [DataContext メソッド (O/R デザイナー)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="ded7b-150"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>

