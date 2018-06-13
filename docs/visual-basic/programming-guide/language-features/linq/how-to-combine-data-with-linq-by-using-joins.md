---
title: '方法 : LINQ の結合を使用してデータを結合する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: f0279cc13e938b6f7853ef11fee1ef046f192316
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653456"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>方法 : LINQ の結合を使用してデータを結合する (Visual Basic)
Visual Basic では、`Join`と`Group Join`コレクション間で共通の値に基づく複数のコレクションの内容を結合するために句をクエリします。 これらの値と呼ばれる*キー*値。 リレーショナル データベースの概念に慣れている開発者が認識されます、`Join`としては INNER JOIN 句と`Group Join`として、実際には、左外部結合句。  
  
 このトピックの例を使用してデータを結合する方法はいくつかを示す、`Join`と`Group Join`クエリ句。  
  
## <a name="create-a-project-and-add-sample-data"></a>プロジェクトを作成し、サンプル データを追加  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>サンプル データと種類を含むプロジェクトを作成するには  
  
1.  このトピックのサンプルを実行するには、Visual Studio を開き、新しい Visual Basic コンソール アプリケーション プロジェクトを追加します。 Visual Basic で作成された Module1.vb ファイルをダブルクリックします。  
  
2.  このトピックの使用中で、サンプル、`Person`と`Pet`型と、次のコード例からのデータ。 既定値にこのコードをコピー `Module1` Visual Basic で作成されたモジュール。  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Join 句を使用して、内部結合を実行します。  
 内部結合は、2 つのコレクションからのデータ。 指定したキー値が一致するアイテムが含まれます。 ない、一致する項目、他のコレクションのいずれかのコレクションから項目が除外されます。  
  
 Visual basic での LINQ は内部結合を実行するための 2 つのオプションを提供します。 暗黙の結合と、明示的な結合します。  
  
 暗黙の結合で結合するコレクションの指定、`From`句に一致するキー フィールドを指定して、`Where`句。 Visual Basic は、暗黙的に指定されたキー フィールドに基づく 2 つのコレクションを結合します。  
  
 使用して、明示的な結合を指定することができます、`Join`句どのキーが結合に使用するフィールドを明確にするときにします。 ここで、`Where`もクエリの結果をフィルター処理する句を使用できます。  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Join 句を使用して、Inner Join を実行するには  
  
1.  次のコードを追加、`Module1`両方暗黙的および明示的な内部結合の例を参照するプロジェクトのモジュール。  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group Join 句を使用して、左外部結合を実行します。  
 左外部結合には、結合および結合の右側にあるコレクションからの値が一致するのみの左側にあるコレクションからすべての項目が含まれています。 左側のコレクション内で一致する項目を持たない結合の右側にあるコレクションから項目は、クエリの結果から除外されます。  
  
 `Group Join`句実行すると、実際には、左外部結合します。 LEFT OUTER JOIN と通常呼ばれるものと新機能の違い、`Group Join`される句を返します、`Group Join`左側にあるコレクション内の各項目の結合の右側にあるコレクションから句のグループの結果。 リレーショナル データベースでは、LEFT OUTER JOIN は、クエリ内の各項目の結果をグループに属していない結果には、結合に両方のコレクションから一致する項目が含まれています。 を返します。 この場合、結合の左側のコレクションからアイテムは、右側のコレクションから一致する項目ごとに繰り返されます。 これがどのように、次の手順を完了したときに表示されます。  
  
 結果を取得することができます、`Group Join`それぞれグループ化されたクエリの結果の項目を返すようにクエリを拡張することによってグループ化されていない結果としてクエリ。 これを実現するにはに対するクエリを実行することを確認する必要がある、`DefaultIfEmpty`グループ化されたコレクションのメソッドです。 これにより、結合の左側のコレクションから項目が右側のコレクションから一致する結果があるない場合でも、クエリ結果に含まれるもします。 コードは、結合の右側のコレクションに一致する値がない場合は、既定の結果値を提供するクエリを追加することができます。  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group Join 句を使用して左外部結合を実行するには  
  
1.  次のコードを追加、`Module1`モジュールで、プロジェクトの両方のグループ化された左外部結合とグループに属していない左外部結合の例を参照してください。  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>複合キーを使用して、結合を実行します。  
 使用することができます、`And`でキーワード、`Join`または`Group Join`句に一致するときに使用する複数のキー フィールドを識別する値の結合するコレクション。 `And`キーワードは、すべての指定キー フィールドに結合する項目の一致する必要がありますを指定します。  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>複合キーを使用して結合を実行するには  
  
1.  次のコードを追加、`Module1`複合キーを使用する結合の例を参照するプロジェクトのモジュール。  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>コードを実行します。  
  
#### <a name="to-add-code-to-run-the-examples"></a>例を実行するコードを追加するには  
  
1.  置換、`Sub Main`で、`Module1`をこのトピックの例を実行する次のコード プロジェクト内のモジュール。  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  F5 キーを押してサンプルを実行します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [From 句](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [WHERE 句](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ によるデータ変換 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
