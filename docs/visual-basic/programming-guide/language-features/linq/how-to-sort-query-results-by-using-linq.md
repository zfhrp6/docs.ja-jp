---
title: "How to: Sort Query Results by Using LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "sorting query results, multiple columns"
  - "sorting data [Visual Basic]"
  - "sorting data [LINQ in Visual Basic]"
  - "sorting query results [LINQ in Visual Basic]"
  - "queries [LINQ in Visual Basic], sorting results"
  - "querying databases [LINQ]"
  - "queries [LINQ in Visual Basic], how-to topics"
  - "query samples [Visual Basic]"
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# How to: Sort Query Results by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

統合言語クエリ \(LINQ: Language\-Integrated Query\) を使用すると、データベース情報へのアクセスとクエリの実行を容易に行うことができます。  
  
 次の例では、新しいアプリケーションを作成して、SQL Server データベースに対するクエリを実行し、`Order By` 句によってクエリ結果を複数のフィールドに基づいて並べ替える方法を示します。  各フィールドの並べ替え順序は、昇順にすることも降順にすることもできます。  詳細については、「[Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。  開発用コンピューターに Northwind サンプル データベースがインストールされていない場合は、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) の Web サイトからダウンロードできます。  手順については、「[Downloading Sample Databases](../Topic/Downloading%20Sample%20Databases.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### データベースへの接続を作成するには  
  
1.  Visual Studio で、**\[表示\]** メニューの **\[サーバー エクスプローラー\]** または **\[データベース エクスプローラー\]** をクリックして、**サーバー エクスプローラー**または**データベース エクスプローラー**を開きます。  
  
2.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、**\[データ接続\]** を右クリックし、**\[接続の追加\]** をクリックします。  
  
3.  Northwind サンプル データベースへの有効な接続を指定します。  
  
### LINQ to SQL ファイルを含むプロジェクトを追加するには  
  
1.  Visual Studio で、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  プロジェクトの種類として、Visual Basic の **\[Windows フォーム アプリケーション\]** をクリックします。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  **\[LINQ to SQL クラス\]** 項目テンプレートをクリックします。  
  
3.  ファイルに `northwind.dbml` という名前を付けます。  **\[追加\]** をクリックします。  オブジェクト リレーショナル デザイナー \(O\/R デザイナー\) で northwind.dbml ファイルが開かれます。  
  
### 照会するテーブルを O\/R デザイナーに追加するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、Northwind データベースへの接続を展開します。  **\[Tables\]** フォルダーを展開します。  
  
     O\/R デザイナーを閉じている場合は、前に追加した northwind.dbml ファイルをダブルクリックして再度開くことができます。  
  
2.  Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。  Orders テーブルをクリックし、デザイナーの左ペインにドラッグします。  
  
     デザイナーで、プロジェクトの新しい `Customer` オブジェクトと `Order` オブジェクトが作成されます。  デザイナーがテーブル間の関係を自動的に検出し、関連オブジェクトの子プロパティを作成します。  たとえば、IntelliSense では、`Customer` オブジェクトに、その顧客に関連するすべての受注についての `Orders` プロパティが含まれることが示されます。  
  
3.  変更を保存し、デザイナーを閉じます。  
  
4.  プロジェクトを保存します。  
  
### データベースを照会するコードを追加し、結果を表示するには  
  
1.  **ツールボックス**から、<xref:System.Windows.Forms.DataGridView> コントロールを、プロジェクトの既定の Windows フォームである Form1 にドラッグします。  
  
2.  Form1 をダブルクリックして、フォームの `Load` イベントのコードを追加します。  
  
3.  O\/R デザイナーにテーブルを追加すると、デザイナーによって <xref:System.Data.Linq.DataContext> オブジェクトがプロジェクトに追加されます。  このオブジェクトには、これらのテーブルにアクセスするために必要なコードで、個々のオブジェクトと各テーブルのコレクションにアクセスするためのコードが格納されます。  プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトには、.dbml ファイルの名前に基づいて名前が付けられます。  このプロジェクトの場合、<xref:System.Data.Linq.DataContext> オブジェクトの名前は `northwindDataContext` になります。  
  
     コード内に <xref:System.Data.Linq.DataContext> のインスタンスを作成し、O\/R デザイナーで指定したテーブルを照会できます。  
  
     データ コンテキストのプロパティとして公開されるテーブルを照会し、その結果を並べ替えるには、`Load` イベントに次のコードを追加します。  このクエリでは、顧客の受注数に基づいて結果が降順に並べ替えられます。  受注数が同じ顧客は、会社名に基づいて昇順 \(既定\) で並べ替えられます。  
  
     [!code-vb[VbLINQToSQLHowTos#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form4.vb#10)]  
  
4.  F5 キーを押してプロジェクトを実行し、結果を確認します。  
  
## 参照  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)