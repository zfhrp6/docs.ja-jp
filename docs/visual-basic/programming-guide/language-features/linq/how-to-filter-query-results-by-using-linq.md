---
title: '方法 : LINQ を使用してクエリ結果をフィルター処理する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 8e051d583cdaeb04190e4499834a052fa41d1c48
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827210"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>方法 : LINQ を使用してクエリ結果をフィルター処理する (Visual Basic)
統合言語クエリ (LINQ) では、簡単にデータベース情報にアクセスしてクエリを実行します。  
  
 次の例は、SQL Server データベースに対してクエリを実行し、特定の値によって結果をフィルター処理を使用して、新しいアプリケーションを作成する方法を示します、`Where`句。 詳細については、次を参照してください。 [Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)です。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューターにこのデータベースがいない場合は、Microsoft ダウンロード センターからダウンロードできます。 手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1.  Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。  
  
2.  右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**です。  
  
3.  Northwind サンプル データベースへの接続を有効なを指定します。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL ファイルを含むプロジェクトを追加するのには  
  
1.  Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。 Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレート。  
  
3.  そのファイルに `northwind.dbml` という名前を付けます。 **[追加]** をクリックします。 オブジェクト リレーショナル デザイナー (O/R デザイナー) は、northwind.dbml ファイルを開きます。  
  
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
  
     次のコードを追加、`Load`データ コンテキストのプロパティとして公開されているテーブルを照会するイベントです。 クエリの結果をフィルター処理およびに配置されている顧客だけを返します`London`です。  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  F5 キーを押してプロジェクトを実行し、結果を表示します。  
  
5.  試用できるその他の一部のフィルターを次に示します。  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
