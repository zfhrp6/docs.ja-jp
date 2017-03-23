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
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 44ca3e44d8411a6329d176eb778677bfab2b365c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>方法 : LINQ を使用してデータベースのデータを変更する (Visual Basic)
統合言語クエリ (LINQ) クエリを行う簡単にデータベース情報にアクセスして、データベース内の値を変更します。  
  
 次の例では、SQL Server データベースを取得する新しいアプリケーションを作成する方法と更新プログラムの情報を示します。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューターに Northwind サンプル データベースがないをからダウンロードできます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。 手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1.  Visual Studio で開きます**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして、**ビュー** ] メニューの [クリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
2.  右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、 をクリック**接続の追加**します。  
  
3.  Northwind サンプル データベースに有効な接続を指定します。  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>SQL ファイルに、LINQ では、プロジェクトを追加するには  
  
1.  Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。 Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレートです。  
  
3.  そのファイルに `northwind.dbml` という名前を付けます。 **[追加]**をクリックします。 オブジェクト リレーショナル デザイナー (O/R デザイナー) を開いて、`northwind.dbml`ファイルです。  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>クエリを実行し、デザイナーを変更するテーブルを追加するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。 展開、**テーブル**フォルダーです。  
  
     O/R デザイナーを閉じていた場合をダブルクリックして開くことができます、`northwind.dbml`前に追加したファイルです。  
  
2.  Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。  
  
     デザイナーでは、プロジェクトの新しい Customer オブジェクトを作成します。  
  
3.  変更内容を保存してデザイナーを閉じます。  
  
4.  プロジェクトを保存します。  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>データベースを変更し、結果を表示するコードを追加するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>コントロールをプロジェクトの Form1 の既定の Windows フォームにします</xref:System.Windows.Forms.DataGridView>。  
  
2.  O/R デザイナーにテーブルを追加したときに、デザイナーが追加、<xref:System.Data.Linq.DataContext>オブジェクトをプロジェクトにします</xref:System.Data.Linq.DataContext>。 このオブジェクトには、Customers テーブルにアクセスするのに使用できるコードが含まれています。 また、ローカルの Customer オブジェクトと、テーブルの顧客のコレクションを定義するコードも含まれます。 <xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいての .dbml ファイルの名前</xref:System.Data.Linq.DataContext>。 このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`</xref:System.Data.Linq.DataContext>。  
  
     インスタンスを作成することができます、<xref:System.Data.Linq.DataContext>コードとクエリ内のオブジェクトおよび O/R デザイナーで指定された顧客のコレクションを変更します</xref:System.Data.Linq.DataContext>。 呼び出して送信するまで、顧客のコレクションに加えた変更はデータベースに反映されませんが、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>のメソッド、<xref:System.Data.Linq.DataContext>オブジェクト</xref:System.Data.Linq.DataContext></xref:System.Data.Linq.DataContext.SubmitChanges%2A>。  
  
     <xref:System.Windows.Forms.Form.Load> <xref:System.Data.Linq.DataContext>。</xref:System.Data.Linq.DataContext>のプロパティとして公開される Customers テーブルを照会するイベント</xref:System.Windows.Forms.Form.Load>にコードを追加する Windows フォーム、Form1 をダブルクリックします。 次のコードを追加します。  
  
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
  
3.  **ツールボックス**、3 つをドラッグして<xref:System.Windows.Forms.Button>をフォームにコントロールできます</xref:System.Windows.Forms.Button>。 最初の選択`Button`コントロールです。 **プロパティ**ウィンドウで、設定、`Name`の`Button`に制御を`AddButton`と`Text`に`Add`します。 2 番目のボタンを選択し、設定、`Name`プロパティを`UpdateButton`と`Text`プロパティを`Update`します。 3 番目のボタンを選択し、設定、`Name`プロパティを`DeleteButton`と`Text`プロパティを`Delete`します。  
  
4.  ダブルクリックして、**追加**にコードを追加するボタン、`Click`イベントです。 次のコードを追加します。  
  
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
  
5.  ダブルクリックして、**更新**にコードを追加するボタン、`Click`イベントです。 次のコードを追加します。  
  
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
  
6.  ダブルクリックして、**削除**にコードを追加するボタン、`Click`イベントです。 次のコードを追加します。  
  
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
  
7.  F5 キーを押してプロジェクトを実行します。 クリックして**追加**新しいレコードを追加します。 クリックして**更新**新しいレコードを変更します。 クリックして**削除**新しいレコードを削除します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)   
 [DataContext メソッド (O/R デザイナー)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)   
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
