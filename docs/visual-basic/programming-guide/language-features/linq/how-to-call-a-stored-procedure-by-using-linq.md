---
title: "How to: Call a Stored Procedure by Using LINQ (Visual Basic) | Microsoft Docs"
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
  - "queries [LINQ in Visual Basic], stored procedure calls"
  - "stored procedures sample [Visual Basic]"
  - "stored procedures [LINQ to SQL]"
  - "queries [LINQ in Visual Basic], how-to topics"
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Call a Stored Procedure by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

統合言語クエリ \(LINQ: Language\-Integrated Query\) を使用すると、データベース情報に簡単にアクセスできます。この情報には、ストアド プロシージャなどのデータベース オブジェクトも含まれます。  
  
 次の例は、SQL Server データベース内のストアド プロシージャを呼び出すアプリケーションの作成方法を示します。  このサンプルでは、データベース内の 2 つの異なるストアド プロシージャを呼び出す方法を示します。  それぞれのプロシージャが、クエリの結果を返します。  片方のプロシージャでは入力パラメーターを使用し、他方のプロシージャではパラメーターは使用しません。  
  
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
  
### ストアド プロシージャを O\/R デザイナーに追加するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、Northwind データベースへの接続を展開します。  **\[ストアド プロシージャ\]** フォルダーを展開します。  
  
     O\/R デザイナーを閉じている場合は、前に追加した northwind.dbml ファイルをダブルクリックして再度開くことができます。  
  
2.  **Sales by Year** ストアド プロシージャをクリックし、デザイナーの右ペインにドラッグします。  **Ten Most Expensive Products** ストアド プロシージャをクリックし、デザイナーの右ペインにドラッグします。  
  
3.  変更を保存し、デザイナーを閉じます。  
  
4.  プロジェクトを保存します。  
  
### ストアド プロシージャの結果を表示するコードを追加するには  
  
1.  **ツールボックス**から、<xref:System.Windows.Forms.DataGridView> コントロールを、プロジェクトの既定の Windows フォームである Form1 にドラッグします。  
  
2.  Form1 をダブルクリックし、フォームの `Load` イベントにコードを追加します。  
  
3.  O\/R デザイナーにストアド プロシージャを追加すると、デザイナーによってプロジェクト用の <xref:System.Data.Linq.DataContext> オブジェクトが追加されます。  このオブジェクトには、これらのプロシージャにアクセスするために必要なコードが格納されます。  プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトには、.dbml ファイルの名前に基づいて名前が付けられます。  このプロジェクトの場合、<xref:System.Data.Linq.DataContext> オブジェクトの名前は `northwindDataContext` になります。  
  
     コード内に <xref:System.Data.Linq.DataContext> のインスタンスを作成し、O\/R デザイナーで指定したストアド プロシージャのメソッドを呼び出すことができます。  <xref:System.Windows.Forms.DataGridView> オブジェクトをバインドするには、ストアド プロシージャの結果に対して <xref:System.Linq.Enumerable.ToList%2A> メソッドを呼び出すことで、クエリを直ちに実行する必要があります。  
  
     データ コンテキストのメソッドとして公開されたいずれかのストアド プロシージャを呼び出すには、次のコードを `Load` イベントに追加します。  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/StoredProcedureHowTo/Form3.vb#2)]  
  
4.  F5 キーを押してプロジェクトを実行し、結果を確認します。  
  
## 参照  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)