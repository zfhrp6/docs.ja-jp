---
title: "方法: 特定の型 (Visual Basic) での LINQ クエリ結果を返す |Microsoft ドキュメント"
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
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: 8
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
ms.openlocfilehash: ecbc691a0afeb7ba631949684a0457d9bcdb2728
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="53d34-102">方法 : LINQ クエリ結果を特定の型で返す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53d34-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="53d34-103">統合言語クエリ (LINQ) により、簡単にデータベース情報にアクセスし、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="53d34-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="53d34-104">既定では、LINQ クエリは、匿名型としてオブジェクトの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="53d34-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="53d34-105">クエリを使用して、特定の種類の一覧を返すことを指定することも、`Select`句。</span><span class="sxs-lookup"><span data-stu-id="53d34-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="53d34-106">次の例では、新しいアプリケーションは SQL Server データベースに対してクエリを実行し、結果を特定の名前付きの型を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="53d34-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="53d34-107">詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)と[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="53d34-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="53d34-108">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="53d34-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="53d34-109">開発用コンピューターに Northwind サンプル データベースがないをからダウンロードできます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="53d34-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="53d34-110">手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。</span><span class="sxs-lookup"><span data-stu-id="53d34-110">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="53d34-111">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="53d34-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="53d34-112">Visual Studio で開きます**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="53d34-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="53d34-113">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**します。</span><span class="sxs-lookup"><span data-stu-id="53d34-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="53d34-114">Northwind サンプル データベースに有効な接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="53d34-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="53d34-115">LINQ to SQL ファイルを含むプロジェクトを追加するのには</span><span class="sxs-lookup"><span data-stu-id="53d34-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="53d34-116">Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="53d34-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="53d34-117">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="53d34-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="53d34-118">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53d34-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="53d34-119">選択、 **LINQ to SQL クラス**項目テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="53d34-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="53d34-120">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="53d34-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="53d34-121">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53d34-121">Click **Add**.</span></span> <span data-ttu-id="53d34-122">Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。</span><span class="sxs-lookup"><span data-stu-id="53d34-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="53d34-123">O/R デザイナーをクエリにテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="53d34-123">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="53d34-124">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="53d34-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="53d34-125">展開、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="53d34-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="53d34-126">O/R デザイナーを閉じていた場合は、前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="53d34-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="53d34-127">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="53d34-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="53d34-128">デザイナーが、新たに作成`Customer`プロジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="53d34-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="53d34-129">クエリ結果を射影する、`Customer`型または作成する型として。</span><span class="sxs-lookup"><span data-stu-id="53d34-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="53d34-130">このサンプルでは、後の手順で新しい型が作成され、クエリ結果をその型としてすることができます。</span><span class="sxs-lookup"><span data-stu-id="53d34-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3.  <span data-ttu-id="53d34-131">変更内容を保存してデザイナーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="53d34-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="53d34-132">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="53d34-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="53d34-133">データベースを照会し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="53d34-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="53d34-134">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>コントロールをプロジェクトの Form1 の既定の Windows フォームにします</xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="53d34-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="53d34-135">Form1 クラスを変更する Form1 をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="53d34-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3.  <span data-ttu-id="53d34-136">後に、 `End Class` Form1 クラスのステートメントを作成する次のコードを追加する、`CustomerInfo`このサンプルのクエリ結果を保持する型。</span><span class="sxs-lookup"><span data-stu-id="53d34-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     <span data-ttu-id="53d34-137">[!code-vb[VbLINQToSQLHowTos&#16;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="53d34-137">[!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]</span></span>  
  
4.  <span data-ttu-id="53d34-138">O/R デザイナーにテーブルを追加したときに、デザイナーが追加、<xref:System.Data.Linq.DataContext>オブジェクトをプロジェクトにします</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="53d34-138">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="53d34-139">このオブジェクトには、これらのテーブルにアクセスして、個々 のオブジェクトと各テーブルのコレクションにアクセスに必要なコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="53d34-139">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="53d34-140"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいての .dbml ファイルの名前</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="53d34-140">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="53d34-141">このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="53d34-141">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="53d34-142">インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext>O/R デザイナーで指定されたテーブル内のコードとクエリ</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="53d34-142">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="53d34-143">`Load` Form1 クラスのイベントは、データ コンテキストのプロパティとして公開されているテーブルを照会する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="53d34-143">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="53d34-144">`Select`新しいクエリの句が作成されます`CustomerInfo`クエリ結果の項目ごとに匿名型ではなく行型です。</span><span class="sxs-lookup"><span data-stu-id="53d34-144">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     <span data-ttu-id="53d34-145">[!code-vb[VbLINQToSQLHowTos&#15;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="53d34-145">[!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]</span></span>  
  
5.  <span data-ttu-id="53d34-146">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="53d34-146">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d34-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="53d34-147">See Also</span></span>  
 <span data-ttu-id="53d34-148">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="53d34-148">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="53d34-149"> [クエリ](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="53d34-149"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="53d34-150"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="53d34-150"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="53d34-151"> [DataContext メソッド (O/R デザイナー)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="53d34-151"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>

