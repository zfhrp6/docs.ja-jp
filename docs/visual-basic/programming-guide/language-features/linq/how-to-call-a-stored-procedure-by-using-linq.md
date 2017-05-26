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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: abc3970fc5ab6f4a2f4b67b5efa2b19afb07337b
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>方法 : LINQ を使用してストアド プロシージャを呼び出す (Visual Basic)
統合言語クエリ (LINQ) 簡単データベースなどに格納されているオブジェクトのプロシージャを含むデータベース情報にアクセスできます。  
  
 次の例では、SQL Server データベースでストアド プロシージャを呼び出すアプリケーションを作成する方法を示します。 サンプルは、データベース内の&2; つの異なるストアド プロシージャを呼び出す方法を示します。 各手順では、クエリの結果を返します。 1 つのプロシージャは、入力パラメーターとその他のプロシージャはパラメーターを受け取らないです。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューターに Northwind サンプル データベースがないをからダウンロードできます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。 手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1.  Visual Studio で開きます**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**上、**ビュー**メニュー。  
  
2.  右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**します。  
  
3.  Northwind サンプル データベースに有効な接続を指定します。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL ファイルを含むプロジェクトを追加するのには  
  
1.  Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。 Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレートです。  
  
3.  そのファイルに `northwind.dbml` という名前を付けます。 **[追加]**をクリックします。 Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>ストアド プロシージャを O/R デザイナーに追加するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。 展開、**ストアド プロシージャ**フォルダーです。  
  
     O/R デザイナーを閉じていた場合は、前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。  
  
2.  クリックして、**年度別の売り上げ**ストアド プロシージャと、デザイナーの右側のペインにドラッグします。 クリックして、 **10 最も高価な商品**ストアド プロシージャは、デザイナーの右側のペインにドラッグします。  
  
3.  変更内容を保存してデザイナーを閉じます。  
  
4.  プロジェクトを保存します。  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>ストアド プロシージャの結果を表示するコードを追加するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>コントロールをプロジェクトの Form1 の既定の Windows フォームにします</xref:System.Windows.Forms.DataGridView>。  
  
2.  コードを追加する Form1 をダブルクリックしてその`Load`イベントです。  
  
3.  デザイナーが追加されたストアド プロシージャを O/R デザイナーに追加したときに、 <xref:System.Data.Linq.DataContext>、プロジェクトのオブジェクト</xref:System.Data.Linq.DataContext>。 このオブジェクトには、これらのプロシージャにアクセスするために必要なコードが含まれています。 <xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいての .dbml ファイルの名前</xref:System.Data.Linq.DataContext>。 このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`</xref:System.Data.Linq.DataContext>。  
  
     インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext>O/R デザイナーで指定されたストアド プロシージャ メソッドのコードと呼び出し内</xref:System.Data.Linq.DataContext>。 バインドする、<xref:System.Windows.Forms.DataGridView>オブジェクトのクエリを強制的に呼び出すことによってすぐに実行する必要があります、<xref:System.Linq.Enumerable.ToList%2A>メソッドをストアド プロシージャの結果</xref:System.Linq.Enumerable.ToList%2A></xref:System.Windows.Forms.DataGridView>。  
  
     次のコードを追加、`Load`データ コンテキストのメソッドとして公開されたストアド プロシージャのいずれかを呼び出すイベントです。  
  
     [!code-vb[VbLINQtoSQLHowTos&#1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos&#2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  F5 キーを押してプロジェクトを実行し、結果を表示します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)   
 [DataContext メソッド (O/R デザイナー)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)   
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)

