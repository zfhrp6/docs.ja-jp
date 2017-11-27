---
title: "方法 : LINQ を使用したクエリ結果内の最小値と最大値の検索 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1af5b590310e966f7d27c02e2835a9e959f40c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>方法 : LINQ を使用したクエリ結果内の最小値と最大値の検索 (Visual Basic)
統合言語クエリ (LINQ) では、簡単にデータベース情報にアクセスしてクエリを実行します。  
  
 次の例では、SQL Server データベースに対してクエリを実行する新しいアプリケーションを作成する方法を示します。 このサンプルを使用して結果の最小値と最大値を決定する、`Aggregate`と`Group By`句。 詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)です。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューター上に Northwind サンプル データベースがないことからダウンロードする、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088) Web サイトです。 手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)です。  
  
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
  
3.  O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>プロジェクトのオブジェクト。 このオブジェクトには、個々 のオブジェクトと各テーブルのコレクションだけでなく、それらのテーブルへのアクセスに必要なコードが含まれています。 <xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。 このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。  
  
     インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーで指定されたテーブル内のコードとクエリ。  
  
     次のコードを追加、`Load`イベント。 このコードは、データ コンテキストのプロパティとして公開され、結果の最小値と最大値を決定するテーブルを照会します。 サンプルでは、彼は使用`Aggregate`句を 1 つの結果のクエリと`Group By`の平均値を表示する句の結果をグループ化します。  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  F5 キーを押してプロジェクトを実行し、結果を表示します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
 [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
