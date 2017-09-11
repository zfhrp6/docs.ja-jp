---
title: "方法: LINQ (Visual Basic) を使用してストアド プロシージャを呼び出す |Microsoft ドキュメント"
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
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: 12
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
ms.openlocfilehash: 40e72ece8399b1ffbe8c5457c63113d563c9f7f8
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="5fda5-102">方法 : LINQ を使用してストアド プロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fda5-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="5fda5-103">統合言語クエリ (LINQ) 簡単データベースなどに格納されているオブジェクトのプロシージャを含むデータベース情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5fda5-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="5fda5-104">次の例では、SQL Server データベースでストアド プロシージャを呼び出すアプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="5fda5-105">サンプルは、データベース内の&2; つの異なるストアド プロシージャを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="5fda5-106">各手順では、クエリの結果を返します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="5fda5-107">1 つのプロシージャは、入力パラメーターとその他のプロシージャはパラメーターを受け取らないです。</span><span class="sxs-lookup"><span data-stu-id="5fda5-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="5fda5-108">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="5fda5-109">開発用コンピューターに Northwind サンプル データベースがないをからダウンロードできます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="5fda5-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="5fda5-110">手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-110">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="5fda5-111">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="5fda5-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="5fda5-112">Visual Studio で開きます**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="5fda5-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="5fda5-113">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="5fda5-114">Northwind サンプル データベースに有効な接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="5fda5-115">LINQ to SQL ファイルを含むプロジェクトを追加するのには</span><span class="sxs-lookup"><span data-stu-id="5fda5-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="5fda5-116">Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="5fda5-117">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="5fda5-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="5fda5-118">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5fda5-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="5fda5-119">選択、 **LINQ to SQL クラス**項目テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="5fda5-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="5fda5-120">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5fda5-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="5fda5-121">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5fda5-121">Click **Add**.</span></span> <span data-ttu-id="5fda5-122">Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。</span><span class="sxs-lookup"><span data-stu-id="5fda5-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="5fda5-123">ストアド プロシージャを O/R デザイナーに追加するには</span><span class="sxs-lookup"><span data-stu-id="5fda5-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="5fda5-124">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="5fda5-125">展開、**ストアド プロシージャ**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="5fda5-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="5fda5-126">O/R デザイナーを閉じていた場合は、前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="5fda5-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="5fda5-127">クリックして、**年度別の売り上げ**ストアド プロシージャと、デザイナーの右側のペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5fda5-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="5fda5-128">クリックして、 **10 最も高価な商品**ストアド プロシージャは、デザイナーの右側のペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5fda5-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="5fda5-129">変更内容を保存してデザイナーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5fda5-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="5fda5-130">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="5fda5-131">ストアド プロシージャの結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="5fda5-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="5fda5-132">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>コントロールをプロジェクトの Form1 の既定の Windows フォームにします</xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="5fda5-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="5fda5-133">コードを追加する Form1 をダブルクリックしてその`Load`イベントです。</span><span class="sxs-lookup"><span data-stu-id="5fda5-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="5fda5-134">デザイナーが追加されたストアド プロシージャを O/R デザイナーに追加したときに、 <xref:System.Data.Linq.DataContext>、プロジェクトのオブジェクト</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="5fda5-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="5fda5-135">このオブジェクトには、これらのプロシージャにアクセスするために必要なコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5fda5-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="5fda5-136"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいての .dbml ファイルの名前</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="5fda5-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="5fda5-137">このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="5fda5-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="5fda5-138">インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext>O/R デザイナーで指定されたストアド プロシージャ メソッドのコードと呼び出し内</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="5fda5-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="5fda5-139">バインドする、<xref:System.Windows.Forms.DataGridView>オブジェクトのクエリを強制的に呼び出すことによってすぐに実行する必要があります、<xref:System.Linq.Enumerable.ToList%2A>メソッドをストアド プロシージャの結果</xref:System.Linq.Enumerable.ToList%2A></xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="5fda5-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="5fda5-140">次のコードを追加、`Load`データ コンテキストのメソッドとして公開されたストアド プロシージャのいずれかを呼び出すイベントです。</span><span class="sxs-lookup"><span data-stu-id="5fda5-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     <span data-ttu-id="5fda5-141">[!code-vb[VbLINQtoSQLHowTos&#1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5fda5-141">[!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]</span></span>  
    <span data-ttu-id="5fda5-142">[!code-vb[VbLINQtoSQLHowTos&#2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5fda5-142">[!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]</span></span>  
  
4.  <span data-ttu-id="5fda5-143">F5 キーを押してプロジェクトを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="5fda5-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fda5-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fda5-144">See Also</span></span>  
 <span data-ttu-id="5fda5-145">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="5fda5-145">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="5fda5-146"> [クエリ](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="5fda5-146"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="5fda5-147"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="5fda5-147"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="5fda5-148"> [DataContext メソッド (O/R デザイナー)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span><span class="sxs-lookup"><span data-stu-id="5fda5-148"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span></span>  
<span data-ttu-id="5fda5-149"> [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span><span class="sxs-lookup"><span data-stu-id="5fda5-149"> [How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span></span>

