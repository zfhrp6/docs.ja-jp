---
title: "方法: LINQ (Visual Basic) を使用して、データベース内のデータの変更 |Microsoft ドキュメント"
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
caps.latest.revision: 15
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2d230594345cff26a83907714e5e8e11b10dde60
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="36530-102">方法 : LINQ を使用してデータベースのデータを変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36530-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="36530-103">統合言語クエリ (LINQ) クエリを行う簡単にデータベース情報にアクセスして、データベース内の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="36530-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="36530-104">次の例では、SQL Server データベースを取得する新しいアプリケーションを作成する方法と更新プログラムの情報を示します。</span><span class="sxs-lookup"><span data-stu-id="36530-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="36530-105">このトピックの例では、Northwind サンプル データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="36530-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="36530-106">開発用コンピューターに Northwind サンプル データベースがないをからダウンロードできます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="36530-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="36530-107">手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。</span><span class="sxs-lookup"><span data-stu-id="36530-107">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="36530-108">データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="36530-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="36530-109">Visual Studio で開きます**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして、**ビュー** ] メニューの [クリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="36530-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="36530-110">右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、 をクリック**接続の追加**します。</span><span class="sxs-lookup"><span data-stu-id="36530-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="36530-111">Northwind サンプル データベースに有効な接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="36530-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="36530-112">SQL ファイルに、LINQ では、プロジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="36530-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="36530-113">Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="36530-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="36530-114">Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。</span><span class="sxs-lookup"><span data-stu-id="36530-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="36530-115">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36530-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="36530-116">選択、 **LINQ to SQL クラス**項目テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="36530-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="36530-117">そのファイルに `northwind.dbml` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="36530-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="36530-118">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36530-118">Click **Add**.</span></span> <span data-ttu-id="36530-119">オブジェクト リレーショナル デザイナー (O/R デザイナー) を開いて、`northwind.dbml`ファイルです。</span><span class="sxs-lookup"><span data-stu-id="36530-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="36530-120">クエリを実行し、デザイナーを変更するテーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="36530-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="36530-121">**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。</span><span class="sxs-lookup"><span data-stu-id="36530-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="36530-122">展開、**テーブル**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="36530-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="36530-123">O/R デザイナーを閉じていた場合をダブルクリックして開くことができます、`northwind.dbml`前に追加したファイルです。</span><span class="sxs-lookup"><span data-stu-id="36530-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="36530-124">Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="36530-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="36530-125">デザイナーでは、プロジェクトの新しい Customer オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="36530-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="36530-126">変更内容を保存してデザイナーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36530-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="36530-127">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="36530-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="36530-128">データベースを変更し、結果を表示するコードを追加するには</span><span class="sxs-lookup"><span data-stu-id="36530-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="36530-129">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>コントロールをプロジェクトの Form1 の既定の Windows フォームにします</xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="36530-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="36530-130">O/R デザイナーにテーブルを追加したときに、デザイナーが追加、<xref:System.Data.Linq.DataContext>オブジェクトをプロジェクトにします</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="36530-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="36530-131">このオブジェクトには、Customers テーブルにアクセスするのに使用できるコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="36530-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="36530-132">また、ローカルの Customer オブジェクトと、テーブルの顧客のコレクションを定義するコードも含まれます。</span><span class="sxs-lookup"><span data-stu-id="36530-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="36530-133"><xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいての .dbml ファイルの名前</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="36530-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="36530-134">このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="36530-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="36530-135">インスタンスを作成することができます、<xref:System.Data.Linq.DataContext>コードとクエリ内のオブジェクトおよび O/R デザイナーで指定された顧客のコレクションを変更します</xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="36530-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="36530-136">呼び出して送信するまで、顧客のコレクションに加えた変更はデータベースに反映されませんが、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>のメソッド、<xref:System.Data.Linq.DataContext>オブジェクト</xref:System.Data.Linq.DataContext></xref:System.Data.Linq.DataContext.SubmitChanges%2A>。</span><span class="sxs-lookup"><span data-stu-id="36530-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="36530-137"><xref:System.Windows.Forms.Form.Load> <xref:System.Data.Linq.DataContext>。</xref:System.Data.Linq.DataContext>のプロパティとして公開される Customers テーブルを照会するイベント</xref:System.Windows.Forms.Form.Load>にコードを追加する Windows フォーム、Form1 をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="36530-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="36530-138">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="36530-138">Add the following code:</span></span>  
  
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
  
3.  <span data-ttu-id="36530-139">**ツールボックス**、3 つをドラッグして<xref:System.Windows.Forms.Button>をフォームにコントロールできます</xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="36530-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="36530-140">最初の選択`Button`コントロールです。</span><span class="sxs-lookup"><span data-stu-id="36530-140">Select the first `Button` control.</span></span> <span data-ttu-id="36530-141">**プロパティ**ウィンドウで、設定、`Name`の`Button`に制御を`AddButton`と`Text`に`Add`します。</span><span class="sxs-lookup"><span data-stu-id="36530-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="36530-142">2 番目のボタンを選択し、設定、`Name`プロパティを`UpdateButton`と`Text`プロパティを`Update`します。</span><span class="sxs-lookup"><span data-stu-id="36530-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="36530-143">3 番目のボタンを選択し、設定、`Name`プロパティを`DeleteButton`と`Text`プロパティを`Delete`します。</span><span class="sxs-lookup"><span data-stu-id="36530-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="36530-144">ダブルクリックして、**追加**にコードを追加するボタン、`Click`イベントです。</span><span class="sxs-lookup"><span data-stu-id="36530-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="36530-145">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="36530-145">Add the following code:</span></span>  
  
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
  
5.  <span data-ttu-id="36530-146">ダブルクリックして、**更新**にコードを追加するボタン、`Click`イベントです。</span><span class="sxs-lookup"><span data-stu-id="36530-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="36530-147">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="36530-147">Add the following code:</span></span>  
  
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
  
6.  <span data-ttu-id="36530-148">ダブルクリックして、**削除**にコードを追加するボタン、`Click`イベントです。</span><span class="sxs-lookup"><span data-stu-id="36530-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="36530-149">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="36530-149">Add the following code:</span></span>  
  
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
  
7.  <span data-ttu-id="36530-150">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="36530-150">Press F5 to run your project.</span></span> <span data-ttu-id="36530-151">クリックして**追加**新しいレコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="36530-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="36530-152">クリックして**更新**新しいレコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="36530-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="36530-153">クリックして**削除**新しいレコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="36530-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36530-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="36530-154">See Also</span></span>  
 <span data-ttu-id="36530-155">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="36530-155">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="36530-156"> [クエリ](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="36530-156"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="36530-157"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="36530-157"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="36530-158"> [DataContext メソッド (O/R デザイナー)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span><span class="sxs-lookup"><span data-stu-id="36530-158"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span></span>  
<span data-ttu-id="36530-159"> [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span><span class="sxs-lookup"><span data-stu-id="36530-159"> [How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span></span>
