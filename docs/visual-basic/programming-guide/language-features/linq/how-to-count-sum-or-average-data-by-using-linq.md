---
title: "方法: カウント、合計、または LINQ (Visual Basic) を使用して平均データ |Microsoft ドキュメント"
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
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
caps.latest.revision: 9
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
ms.openlocfilehash: 63ea6cd9eb2942ac80688cec6ea44e89c2a2b7f7
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="fe600-102">方法 : LINQ を使用したデータの数、合計、または平均の算出 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe600-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="fe600-103">統合言語クエリ (LINQ) により、簡単にデータベース情報にアクセスし、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="fe600-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="fe600-104">次の例では、SQL Server データベースに対してクエリを実行する新しいアプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe600-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="fe600-105">サンプル カウント、合計、および結果の平均値を使用して、`Aggregate`と`Group By`句。</span><span class="sxs-lookup"><span data-stu-id="fe600-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="fe600-106">詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="fe600-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="fe600-107">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe600-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="fe600-108">開発用コンピューターに Northwind サンプル データベースがないをからダウンロードできます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="fe600-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="fe600-109">手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。</span><span class="sxs-lookup"><span data-stu-id="fe600-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="fe600-110">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="fe600-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="fe600-111">Visual Studio で開きます**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="fe600-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="fe600-112">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**します。</span><span class="sxs-lookup"><span data-stu-id="fe600-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="fe600-113">Northwind サンプル データベースに有効な接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="fe600-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="fe600-114">LINQ to SQL ファイルを含むプロジェクトを追加するのには</span><span class="sxs-lookup"><span data-stu-id="fe600-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="fe600-115">Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="fe600-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="fe600-116">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="fe600-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="fe600-117">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe600-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="fe600-118">選択、 **LINQ to SQL クラス**項目テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="fe600-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="fe600-119">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="fe600-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="fe600-120">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe600-120">Click **Add**.</span></span> <span data-ttu-id="fe600-121">Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。</span><span class="sxs-lookup"><span data-stu-id="fe600-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="fe600-122">O/R デザイナーをクエリにテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="fe600-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="fe600-123">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="fe600-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="fe600-124">展開、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="fe600-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="fe600-125">O/R デザイナーを閉じていた場合は、前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="fe600-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="fe600-126">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="fe600-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="fe600-127">Orders テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="fe600-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="fe600-128">デザイナーを新規作成`Customer`と`Order`プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fe600-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="fe600-129">デザイナーが自動的にテーブル間のリレーションシップを検出し、関連オブジェクトのプロパティの子を作成することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fe600-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="fe600-130">たとえば、IntelliSense が表示されますが、`Customer`オブジェクトには、`Orders`その顧客に関連するすべての発注書のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="fe600-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="fe600-131">変更内容を保存してデザイナーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fe600-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="fe600-132">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="fe600-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="fe600-133">データベースを照会し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="fe600-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="fe600-134">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>コントロールをプロジェクトの Form1 の既定の Windows フォームにします</xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="fe600-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="fe600-135">コードを追加する Form1 をダブルクリックして、`Load`形式のイベントです。</span><span class="sxs-lookup"><span data-stu-id="fe600-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="fe600-136">O/R デザイナーにテーブルを追加したときに、デザイナーが追加、 <xref:System.Data.Linq.DataContext>、プロジェクトのオブジェクト</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="fe600-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="fe600-137">このオブジェクトには、これらのテーブルにアクセスして、個々 のオブジェクトと各テーブルのコレクションにアクセスに必要なコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fe600-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="fe600-138"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいての .dbml ファイルの名前</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="fe600-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="fe600-139">このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="fe600-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="fe600-140">インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext>O/R デザイナーで指定されたテーブル内のコードとクエリ</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="fe600-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="fe600-141">次のコードを追加、`Load`のプロパティとして公開されているテーブルを照会するイベント、<xref:System.Data.Linq.DataContext>とカウント、合計、および結果の平均します</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="fe600-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="fe600-142">サンプルを使用、 `Aggregate` 、単一の結果のクエリに句と`Group By`の平均値を表示する句の結果をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="fe600-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     <span data-ttu-id="fe600-143">[!code-vb[VbLINQToSQLHowTos&#13;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fe600-143">[!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]</span></span>  
  
4.  <span data-ttu-id="fe600-144">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="fe600-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe600-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe600-145">See Also</span></span>  
 <span data-ttu-id="fe600-146">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="fe600-146">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="fe600-147"> [クエリ](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="fe600-147"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="fe600-148"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="fe600-148"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="fe600-149"> [DataContext メソッド (O/R デザイナー)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="fe600-149"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>  
<span data-ttu-id="fe600-150"> [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="fe600-150"> [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="fe600-151"> [Group By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)</span><span class="sxs-lookup"><span data-stu-id="fe600-151"> [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md)</span></span>

