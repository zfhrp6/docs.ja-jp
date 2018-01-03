---
title: "方法 : LINQ を使用したデータの数、合計、または平均の算出 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbdc074bef64413b8b25709e48bba49f296ecb95
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>方法 : LINQ を使用したデータの数、合計、または平均の算出 (Visual Basic)
統合言語クエリ (LINQ) では、簡単にデータベース情報にアクセスしてクエリを実行します。  
  
 次の例では、SQL Server データベースに対してクエリを実行する新しいアプリケーションを作成する方法を示します。 サンプルは、カウントの合計を計算しを使用して、結果の平均を計算、`Aggregate`と`Group By`句。 詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)です。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューター上に Northwind サンプル データベースがないことからダウンロードする、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。 手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1.  Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。  
  
2.  右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**です。  
  
3.  Northwind サンプル データベースへの接続を有効なを指定します。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL ファイルを含むプロジェクトを追加するのには  
  
1.  Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。 Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレート。  
  
3.  そのファイルに `northwind.dbml` という名前を付けます。 **[追加]**をクリックします。 Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R デザイナーをクエリにテーブルを追加するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。 展開して、**テーブル**フォルダーです。  
  
     O/R デザイナーが閉じられたかと、以前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。  
  
2.  Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。 Orders テーブルをクリックし、デザイナーの左ペインにドラッグします。  
  
     デザイナーを新規作成`Customer`と`Order`プロジェクトのオブジェクト。 デザイナーが自動的にテーブル間のリレーションシップを検出し、関連オブジェクトのプロパティの子を作成することに注意してください。 たとえば、IntelliSense ことが表示されます、`Customer`オブジェクトには、`Orders`その顧客に関連するすべての注文のプロパティです。  
  
3.  変更を保存し、デザイナーを終了します。  
  
4.  プロジェクトを保存します。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>データベースを照会し、結果を表示するコードを追加するには  
  
1.  **ツールボックス**、ドラッグ、 <xref:System.Windows.Forms.DataGridView> Form1、プロジェクトの既定の Windows フォームにコントロールできます。  
  
2.  コードを追加する Form1 をダブルクリックして、`Load`フォームのイベントです。  
  
3.  O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>プロジェクトのオブジェクト。 このオブジェクトには、これらのテーブルにアクセスして、個々 のオブジェクトと各テーブルのコレクションにアクセスする必要があります、コードが含まれています。 <xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。 このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。  
  
     インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーで指定されたテーブル内のコードとクエリ。  
  
     次のコードを追加、`Load`イベントのプロパティとして公開されているテーブルに対するクエリを<xref:System.Data.Linq.DataContext>とカウント、合計、および結果を平均します。 サンプルを使用、`Aggregate`句を 1 つの結果のクエリと`Group By`の平均値を表示する句の結果をグループ化します。  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  F5 キーを押してプロジェクトを実行し、結果を表示します。  
  
## <a name="see-also"></a>参照  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Group By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)
