---
title: "How to: Count, Sum, or Average Data by Using LINQ (Visual Basic) | Microsoft Docs"
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
  - "average operator [LINQ in Visual Basic]"
  - "aggregate operator [LINQ in Visual Basic]"
  - "aggregate queries"
  - "queries [LINQ in Visual Basic], sum results"
  - "Aggregate clause"
  - "sum operator [LINQ in Visual Basic]"
  - "queries [LINQ in Visual Basic], aggregate queries"
  - "queries [LINQ in Visual Basic], counting results"
  - "querying databases [LINQ]"
  - "queries [LINQ in Visual Basic], how-to topics"
  - "query samples [Visual Basic]"
  - "count operator [LINQ in Visual Basic]"
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

統合言語クエリ \(LINQ: Language\-Integrated Query\) を使用すると、データベース情報へのアクセスとクエリの実行を容易に行うことができます。  
  
 SQL Server データベースに対するクエリを実行する新しいアプリケーションの作成方法の例を以下に示します。  この例は、`Aggregate` 句と `Group By` 句を使用して、結果の数、合計、および平均を算出します。  詳細については、「[Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md)」および「[Group By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)」を参照してください。  
  
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
  
3.  O\/R デザイナーにテーブルを追加すると、デザイナーによってプロジェクトに <xref:System.Data.Linq.DataContext> オブジェクトが追加されます。  このオブジェクトには、これらのテーブルにアクセスするために必要なコードで、個々のオブジェクトと各テーブルのコレクションにアクセスするためのコードが格納されます。  プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトには、.dbml ファイルの名前に基づいて名前が付けられます。  このプロジェクトの場合、<xref:System.Data.Linq.DataContext> オブジェクトの名前は `northwindDataContext` になります。  
  
     コード内に <xref:System.Data.Linq.DataContext> のインスタンスを作成し、O\/R デザイナーで指定したテーブルを照会できます。  
  
     <xref:System.Data.Linq.DataContext> のプロパティとして公開されるテーブルを照会し、その結果の数、合計、および平均を算出するには、次のコードを `Load` イベントに追加します。  この例では、`Aggregate` 句を使用して単一の結果を照会し、`Group By` 句を使用してグループ化された結果の平均を示します。  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form6.vb#13)]  
  
4.  F5 キーを押してプロジェクトを実行し、結果を確認します。  
  
## 参照  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Group By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)