---
title: "How to: Modify Data in a Database by Using LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "inserting rows [LINQ to SQL]"
  - "deleting rows [LINQ to SQL]"
  - "updating rows [LINQ to SQL]"
  - "inserting data [Visual Basic]"
  - "deleting data"
  - "data [Visual Basic], updating"
  - "updating data [LINQ]"
  - "queries [LINQ in Visual Basic], data changes in database"
  - "queries [LINQ in Visual Basic], how-to topics"
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Modify Data in a Database by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

統合言語クエリ \(LINQ: Language\-Integrated Query\) のクエリを使用すると、簡単にデータベースの情報にアクセスし、データベースの値を変更できます。  
  
 SQL Server データベースの情報を取得して更新する新しいアプリケーションの作成方法の例を以下に示します。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。  開発用コンピューターに Northwind サンプル データベースがインストールされていない場合は、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) の Web サイトからダウンロードできます。  手順については、「[Downloading Sample Databases](../Topic/Downloading%20Sample%20Databases.md)」を参照してください。  
  
### データベースへの接続を作成するには  
  
1.  Visual Studio で、**\[表示\]** メニューの **\[サーバー エクスプローラー\]** または **\[データベース エクスプローラー\]** をクリックして、**サーバー エクスプローラー**または**データベース エクスプローラー**を開きます。  
  
2.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、**\[データ接続\]** を右クリックし、**\[接続の追加\]** をクリックします。  
  
3.  Northwind サンプル データベースへの有効な接続を指定します。  
  
### LINQ to SQL ファイルを含むプロジェクトを追加するには  
  
1.  Visual Studio で、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  プロジェクトの種類として、Visual Basic の **\[Windows フォーム アプリケーション\]** をクリックします。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  **\[LINQ to SQL クラス\]** 項目テンプレートをクリックします。  
  
3.  ファイルに `northwind.dbml` という名前を付けます。  **\[追加\]** をクリックします。  オブジェクト リレーショナル デザイナー \(O\/R デザイナー\) で `northwind.dbml` ファイルが開かれます。  
  
### 照会および変更するテーブルをデザイナーに追加するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、Northwind データベースへの接続を展開します。  **\[Tables\]** フォルダーを展開します。  
  
     O\/R デザイナーを閉じている場合は、前に追加した `northwind.dbml` ファイルをダブルクリックして再度開くことができます。  
  
2.  Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。  
  
     デザイナーによって、プロジェクト用の新しい Customer オブジェクトが作成されます。  
  
3.  変更を保存し、デザイナーを閉じます。  
  
4.  プロジェクトを保存します。  
  
### データベースを変更するコードを追加し、結果を表示するには  
  
1.  **ツールボックス**から、<xref:System.Windows.Forms.DataGridView> コントロールを、プロジェクトの既定の Windows フォームである Form1 にドラッグします。  
  
2.  O\/R デザイナーにテーブルを追加すると、デザイナーによって <xref:System.Data.Linq.DataContext> オブジェクトがプロジェクトに追加されます。  このオブジェクトには、Customers テーブルへのアクセスに使用できるコードが含まれます。  また、テーブルのローカル Customer オブジェクトと Customers コレクションを定義するコードも含まれます。  プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトには、.dbml ファイルの名前に基づいて名前が付けられます。  このプロジェクトの場合、<xref:System.Data.Linq.DataContext> オブジェクトの名前は `northwindDataContext` になります。  
  
     コード内に <xref:System.Data.Linq.DataContext> オブジェクトのインスタンスを作成し、O\/R デザイナーで指定した Customers コレクションを照会および変更できます。  Customers コレクションに対する変更は、<xref:System.Data.Linq.DataContext> オブジェクトの <xref:System.Data.Linq.DataContext.SubmitChanges%2A> メソッドを呼び出して送信するまで、データベースには反映されません。  
  
     Windows  フォーム Form1 をダブルクリックし、<xref:System.Data.Linq.DataContext> のプロパティとして公開されている Customers テーブルを照会するためのコードを、<xref:System.Windows.Forms.Form.Load> イベントに追加します。  次のコードを追加します。  
  
    ```vb#  
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
  
3.  **ツールボックス**から 3 つの <xref:System.Windows.Forms.Button> コントロールをフォームにドラッグします。  最初の `Button` コントロールを選択します。  **\[プロパティ\]** ウィンドウで、`Button` コントロールの `Name` を `AddButton` に設定し、`Text` を `Add` に設定します。  2 番目のボタンを選択し、`Name` プロパティを `UpdateButton` に、`Text` プロパティを `Update` にそれぞれ設定します。  3 番目のボタンを選択し、`Name` プロパティを `DeleteButton` に、`Text` プロパティを `Delete` にそれぞれ設定します。  
  
4.  **\[Add\]** ボタンをダブルクリックし、`Click` イベントにコードを追加します。  次のコードを追加します。  
  
    ```vb#  
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
  
5.  **\[Update\]** ボタンをダブルクリックし、`Click` イベントにコードを追加します。  次のコードを追加します。  
  
    ```vb#  
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
  
6.  **\[Delete\]** ボタンをダブルクリックし、`Click` イベントにコードを追加します。  次のコードを追加します。  
  
    ```vb#  
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
  
7.  F5 キーを押してプロジェクトを実行します。  新しいレコードを追加するには、**\[Add\]** をクリックします。  その新しいレコードを変更するには、**\[Update\]** をクリックします。  その新しいレコードを削除するには、**\[Delete\]** をクリックします。  
  
## 参照  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)