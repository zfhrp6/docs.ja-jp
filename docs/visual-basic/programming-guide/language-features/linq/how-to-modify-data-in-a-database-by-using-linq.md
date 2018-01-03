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
ms.openlocfilehash: 66f21b2a47d3890875062bbdf45e1c4507e1d603
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>方法 : LINQ を使用してデータベースのデータを変更する (Visual Basic)
統合言語クエリ (LINQ) クエリを行う簡単にデータベース情報にアクセスして、データベース内の値を変更します。  
  
 次の例では、SQL Server データベースを取得する新しいアプリケーションを作成する方法と更新プログラムの情報を示します。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューター上に Northwind サンプル データベースがないことからダウンロードする、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。 手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)です。  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1.  Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして、**ビュー**メニューをクリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**です。  
  
2.  右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、 をクリック**接続の追加**です。  
  
3.  Northwind サンプル データベースへの接続を有効なを指定します。  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>SQL ファイルに、LINQ でプロジェクトを追加するには  
  
1.  Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。 Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレート。  
  
3.  そのファイルに `northwind.dbml` という名前を付けます。 **[追加]**をクリックします。 に対してオブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれて、`northwind.dbml`ファイル。  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>クエリを実行し、デザイナーを変更するテーブルを追加するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。 展開して、**テーブル**フォルダーです。  
  
     O/R デザイナーが閉じられたかを開くことができますをダブルクリックして、`northwind.dbml`前に追加したファイルです。  
  
2.  Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。  
  
     デザイナーでは、プロジェクトの新しい顧客オブジェクトを作成します。  
  
3.  変更を保存し、デザイナーを終了します。  
  
4.  プロジェクトを保存します。  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>データベースを変更し、結果を表示するコードを追加するには  
  
1.  **ツールボックス**、ドラッグ、 <xref:System.Windows.Forms.DataGridView> Form1、プロジェクトの既定の Windows フォームにコントロールできます。  
  
2.  O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>をプロジェクトにオブジェクト。 このオブジェクトには、顧客テーブルへのアクセスに使用できるコードが含まれています。 ローカルの Customer オブジェクトと、テーブルの顧客のコレクションを定義するコードも含まれています。 <xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。 このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。  
  
     インスタンスを作成することができます、<xref:System.Data.Linq.DataContext>コードとクエリ内のオブジェクトし、O/R デザイナーで指定された顧客のコレクションを変更します。 データベースでは、呼び出すことで送信するまで、顧客のコレクションに対して行った変更は反映されません、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>のメソッド、<xref:System.Data.Linq.DataContext>オブジェクト。  
  
     Windows フォームをダブルクリックして、Form1 のコードを追加、 <xref:System.Windows.Forms.Form.Load> Customers テーブルを照会するイベントがのプロパティとして公開されている、<xref:System.Data.Linq.DataContext>です。 次のコードを追加します。  
  
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
  
3.  **ツールボックス**、3 つをドラッグして<xref:System.Windows.Forms.Button>コントロールをフォームにします。 最初の選択`Button`コントロール。 **プロパティ**ウィンドウで、設定、`Name`の`Button`に制御を`AddButton`と`Text`に`Add`です。 2 番目のボタンを選択し、設定、`Name`プロパティを`UpdateButton`と`Text`プロパティを`Update`です。 3 番目のボタンを選択し、設定、`Name`プロパティを`DeleteButton`と`Text`プロパティを`Delete`です。  
  
4.  ダブルクリックして、**追加**のコードを追加するにはボタンの`Click`イベント。 次のコードを追加します。  
  
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
  
5.  ダブルクリックして、**更新**のコードを追加するにはボタンの`Click`イベント。 次のコードを追加します。  
  
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
  
6.  ダブルクリックして、**削除**のコードを追加するにはボタンの`Click`イベント。 次のコードを追加します。  
  
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
  
7.  F5 キーを押してプロジェクトを実行します。 をクリックして**追加**新しいレコードを追加します。 をクリックして**更新**新しいレコードを変更します。 をクリックして**削除**新しいレコードを削除します。  
  
## <a name="see-also"></a>参照  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
