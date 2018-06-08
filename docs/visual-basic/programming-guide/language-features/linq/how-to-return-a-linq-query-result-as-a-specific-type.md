---
title: '方法 : LINQ クエリ結果を特定の型で返す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 2c3a10ed901832846da058018a91349be0c2495b
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827086"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>方法 : LINQ クエリ結果を特定の型で返す (Visual Basic)
統合言語クエリ (LINQ) では、簡単にデータベース情報にアクセスしてクエリを実行します。 既定では、LINQ クエリは、匿名型としてオブジェクトの一覧を返します。 クエリを使用して、特定の種類の一覧を返すことを指定することも、`Select`句。  
  
 次の例では、SQL Server データベースに対してクエリを実行し、特定の名前付きの型として、結果を射影する新しいアプリケーションを作成する方法を示します。 詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)と[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)です。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューターにこのデータベースがいない場合は、Microsoft ダウンロード センターからダウンロードできます。 手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1.  Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。  
  
2.  右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**です。  
  
3.  Northwind サンプル データベースへの接続を有効なを指定します。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL ファイルを含むプロジェクトを追加するのには  
  
1.  Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。 Visual Basic を選択して**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレート。  
  
3.  そのファイルに `northwind.dbml` という名前を付けます。 **[追加]** をクリックします。 Northwind.dbml ファイルには、オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R デザイナーをクエリにテーブルを追加するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。 展開して、**テーブル**フォルダーです。  
  
     O/R デザイナーが閉じられたかと、以前に追加した northwind.dbml ファイルをダブルクリックして開くことができます。  
  
2.  Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。  
  
     デザイナーが新たに作成`Customer`プロジェクトのオブジェクト。 クエリの結果を射影することができます、`Customer`型または作成した型として。 このサンプルでは、後の手順で新しい型が作成され、クエリの結果がその型をプロジェクトすることがします。  
  
3.  変更を保存し、デザイナーを終了します。  
  
4.  プロジェクトを保存します。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>データベースを照会し、結果を表示するコードを追加するには  
  
1.  **ツールボックス**、ドラッグ、 <xref:System.Windows.Forms.DataGridView> Form1、プロジェクトの既定の Windows フォームにコントロールできます。  
  
2.  Form1 クラスを変更する Form1 をダブルクリックします。  
  
3.  後に、 `End Class` Form1 クラスのステートメントを作成する次のコードを追加する、`CustomerInfo`このサンプルのクエリの結果を保持する型。  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  O/R デザイナーにテーブルを追加すると、デザイナーが追加、<xref:System.Data.Linq.DataContext>をプロジェクトにオブジェクト。 このオブジェクトには、これらのテーブルにアクセスして、個々 のオブジェクトと各テーブルのコレクションにアクセスする必要があります、コードが含まれています。 <xref:System.Data.Linq.DataContext>オブジェクトは、プロジェクトの名前に基づいて、.dbml ファイルの名前。 このプロジェクトの<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。  
  
     インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーで指定されたテーブル内のコードとクエリ。  
  
     `Load` Form1 クラスのイベントは、データ コンテキストのプロパティとして公開されているテーブルを照会する次のコードを追加します。 `Select`新しいクエリの句が作成されます`CustomerInfo`クエリ結果の項目ごとに、匿名型ではなく型です。  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  F5 キーを押してプロジェクトを実行し、結果を表示します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
