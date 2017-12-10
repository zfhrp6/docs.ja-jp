---
title: "方法 : LINQ を使用してデータベースのデータを変更する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69e2fc7a6860ad2ff43742d37cd35671ebe35acf
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="87c0f-102">方法 : LINQ を使用してデータベースのデータを変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c0f-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="87c0f-103">統合言語クエリ (LINQ) クエリを行う簡単にデータベース情報にアクセスして、データベース内の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="87c0f-104">次の例では、SQL Server データベースを取得する新しいアプリケーションを作成する方法と更新プログラムの情報を示します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="87c0f-105">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="87c0f-106">開発用コンピューター上に Northwind サンプル データベースがないことからダウンロードする、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="87c0f-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="87c0f-107">手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。</span><span class="sxs-lookup"><span data-stu-id="87c0f-107">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="87c0f-108">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="87c0f-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="87c0f-109">Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして、**ビュー**メニューをクリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**です。</span><span class="sxs-lookup"><span data-stu-id="87c0f-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="87c0f-110">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、 をクリック**接続の追加**です。</span><span class="sxs-lookup"><span data-stu-id="87c0f-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="87c0f-111">Northwind サンプル データベースへの接続を有効なを指定します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="87c0f-112">SQL ファイルに、LINQ でプロジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="87c0f-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="87c0f-113">Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87c0f-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="87c0f-114">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="87c0f-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="87c0f-115">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87c0f-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="87c0f-116">選択、 **LINQ to SQL クラス**項目テンプレート。</span><span class="sxs-lookup"><span data-stu-id="87c0f-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="87c0f-117">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="87c0f-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="87c0f-118">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87c0f-118">Click **Add**.</span></span> <span data-ttu-id="87c0f-119">に対してオブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれて、`northwind.dbml`ファイル。</span><span class="sxs-lookup"><span data-stu-id="87c0f-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="87c0f-120">クエリを実行し、デザイナーを変更するテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="87c0f-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="87c0f-121">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="87c0f-122">展開して、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="87c0f-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="87c0f-123">O/R デザイナーが閉じられたかを開くことができますをダブルクリックして、`northwind.dbml`前に追加したファイルです。</span><span class="sxs-lookup"><span data-stu-id="87c0f-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="87c0f-124">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="87c0f-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="87c0f-125">デザイナーでは、プロジェクトの新しい顧客オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="87c0f-126">変更を保存し、デザイナーを終了します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="87c0f-127">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="87c0f-128">データベースを変更し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="87c0f-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="87c0f-129">**ツールボックス**、ドラッグ、 <xref:System.Windows.Forms.DataGridView> Form1、プロジェクトの既定の Windows フォームにコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="87c0f-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="87c0f-130">O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>をプロジェクトにオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="87c0f-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="87c0f-131">このオブジェクトには、顧客テーブルへのアクセスに使用できるコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="87c0f-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="87c0f-132">ローカルの Customer オブジェクトと、テーブルの顧客のコレクションを定義するコードも含まれています。</span><span class="sxs-lookup"><span data-stu-id="87c0f-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="87c0f-133"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="87c0f-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="87c0f-134">このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="87c0f-135">インスタンスを作成することができます、<xref:System.Data.Linq.DataContext>コードとクエリ内のオブジェクトし、O/R デザイナーで指定された顧客のコレクションを変更します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="87c0f-136">データベースでは、呼び出すことで送信するまで、顧客のコレクションに対して行った変更は反映されません、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>のメソッド、<xref:System.Data.Linq.DataContext>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="87c0f-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="87c0f-137">Windows フォームをダブルクリックして、Form1 のコードを追加、 <xref:System.Windows.Forms.Form.Load> Customers テーブルを照会するイベントがのプロパティとして公開されている、<xref:System.Data.Linq.DataContext>です。</span><span class="sxs-lookup"><span data-stu-id="87c0f-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="87c0f-138">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-138">Add the following code:</span></span>  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  <span data-ttu-id="87c0f-139">**ツールボックス**、3 つをドラッグして<xref:System.Windows.Forms.Button>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="87c0f-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="87c0f-140">最初の選択`Button`コントロール。</span><span class="sxs-lookup"><span data-stu-id="87c0f-140">Select the first `Button` control.</span></span> <span data-ttu-id="87c0f-141">**プロパティ**ウィンドウで、設定、`Name`の`Button`に制御を`AddButton`と`Text`に`Add`です。</span><span class="sxs-lookup"><span data-stu-id="87c0f-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="87c0f-142">2 番目のボタンを選択し、設定、`Name`プロパティを`UpdateButton`と`Text`プロパティを`Update`です。</span><span class="sxs-lookup"><span data-stu-id="87c0f-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="87c0f-143">3 番目のボタンを選択し、設定、`Name`プロパティを`DeleteButton`と`Text`プロパティを`Delete`です。</span><span class="sxs-lookup"><span data-stu-id="87c0f-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="87c0f-144">ダブルクリックして、**追加**のコードを追加するにはボタンの`Click`イベント。</span><span class="sxs-lookup"><span data-stu-id="87c0f-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="87c0f-145">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-145">Add the following code:</span></span>  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  <span data-ttu-id="87c0f-146">ダブルクリックして、**更新**のコードを追加するにはボタンの`Click`イベント。</span><span class="sxs-lookup"><span data-stu-id="87c0f-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="87c0f-147">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-147">Add the following code:</span></span>  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  <span data-ttu-id="87c0f-148">ダブルクリックして、**削除**のコードを追加するにはボタンの`Click`イベント。</span><span class="sxs-lookup"><span data-stu-id="87c0f-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="87c0f-149">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-149">Add the following code:</span></span>  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  <span data-ttu-id="87c0f-150">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-150">Press F5 to run your project.</span></span> <span data-ttu-id="87c0f-151">をクリックして**追加**新しいレコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="87c0f-152">をクリックして**更新**新しいレコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="87c0f-153">をクリックして**削除**新しいレコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="87c0f-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c0f-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="87c0f-154">See Also</span></span>  
 [<span data-ttu-id="87c0f-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="87c0f-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="87c0f-156">クエリ</span><span class="sxs-lookup"><span data-stu-id="87c0f-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="87c0f-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="87c0f-157">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="87c0f-158">DataContext メソッド (O/R デザイナー)</span><span class="sxs-lookup"><span data-stu-id="87c0f-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="87c0f-159">方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる</span><span class="sxs-lookup"><span data-stu-id="87c0f-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
