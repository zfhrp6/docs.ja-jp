---
title: "基本的なクエリ操作 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 794d77a18b50cc1667fddbad17c46735ae91be26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="basic-query-operations-visual-basic"></a>基本的なクエリ操作 (Visual Basic)
このトピックでは、簡単な概要を[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]Visual Basic、および一般的な種類のクエリで実行する操作の一部に式。 詳細については、次のトピックを参照してください。  
  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [チュートリアル: Visual Basic でのクエリの作成](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>(From) データ ソースを指定します。  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]のクエリでは、まず、クエリを実行するデータ ソースを指定します。 したがって、`From`クエリ内の句が常に早い方です。 クエリ演算子では、選択し、ソースの種類に基づく結果を形成します。  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 `From`句は、データ ソースを指定`customers`、および*範囲変数*、`cust`です。 範囲変数は、クエリ式で実際の反復が発生しないことを除き、ループの反復変数に似ています。 クエリを実行すると、多くの場合を使用して、`For Each`ループ、範囲変数が連続する各要素への参照として機能`customers`します。 `cust` の型はコンパイラで推論できるため、明示的に指定する必要はありません。 明示的に型指定なしに記述されたクエリの例については、次を参照してください。[クエリ操作 (Visual Basic) での型の関係](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)です。  
  
 使用する方法についての詳細、 `From` Visual basic での句を参照してください[From 句](../../../../visual-basic/language-reference/queries/from-clause.md)です。  
  
## <a name="filtering-data-where"></a>データのフィルター処理 (場所)  
 可能性があります、最も一般的なクエリ操作では、ブール式の形式でフィルターを適用するがします。 クエリは、式が true の要素のみを返します。 A`Where`句を使用して、フィルター処理を実行します。 フィルターは、結果のシーケンスに含めるデータ ソース内のどの要素を指定します。 次の例では、アドレスがロンドンの顧客だけが含まれます。  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 などの論理演算子を使用することができます`And`と`Or`でフィルター式を組み合わせて、`Where`句。 たとえば、ロンドン、名前を持つ Devon 顧客のみを返すには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 ロンドンまたはパリから顧客を返すするには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 使用する方法についての詳細、 `Where` Visual basic での句を参照してください[Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)です。  
  
## <a name="ordering-data-order-by"></a>データ (Order By) の順序  
 多くの場合は、特定の順序に返されるデータを並べ替えると便利なです。 `Order By`句は、返されるシーケンスに指定されたフィールドで並べ替えられる要素を発生します。 たとえば、次のクエリがに基づいて結果を並べ替えます、`Name`プロパティです。 `Name`文字列では、A ~ Z から返されたデータは、アルファベット順に並べ替えられます。  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 結果を逆の順序 (Z から A) で並び替えるには、`Order By...Descending` 句を使用します。 既定値は`Ascending`がいずれも`Ascending`も`Descending`を指定します。  
  
 使用する方法についての詳細、 `Order By` Visual basic での句を参照してください[Order By 句](../../../../visual-basic/language-reference/queries/order-by-clause.md)です。  
  
## <a name="selecting-data-select"></a>データ (選択) を選択します。  
 `Select`句は、フォームと返される要素の内容を指定します。 完了の結果が構成されるかどうかを指定するたとえば、`Customer`オブジェクト、1 つだけ`Customer`計算に基づいて、プロパティ、プロパティのサブセット、さまざまなデータ ソース、または新しい結果の種類からのプロパティの組み合わせ。 `Select` 句でソース要素のコピー以外のものを生成する場合、その操作は*投影*と呼ばれます。  
  
 完全なから成るコレクションを取得する`Customer`オブジェクトが、範囲変数自体を選択します。  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 場合、`Customer`インスタンスが、多くのフィールドを持つ大規模なオブジェクトと名前を取得することを選択できます`cust.Name`の次の例に示すようにします。 ローカル型推論のコレクションから結果の型が変更する`Customer`オブジェクトを文字列のコレクション。  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 データ ソースから複数のフィールドを選択するには、2 つの選択肢があります。  
  
-   `Select`句、結果に含めるフィールドを指定します。 コンパイラは、そのプロパティとしてそれらのフィールドを持つ匿名型を定義します。 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
     次の例で返される要素は、匿名型のインスタンスであるため、できませんで参照する型名別の場所、コードでします。 型のコンパイラに指定された名前には、通常の Visual Basic コードで無効な文字が含まれています。 次の例では、クエリでは、によって返されるコレクション内の要素で`londonCusts4`匿名型のインスタンスであります。  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     または  
  
-   結果に含めるを作成し、型のインスタンスを初期化する特定のフィールドを含んでいる名前付きの型を定義、`Select`句。 これらは、返されますが、コレクションの外部の個々 の結果を使用する必要がある場合にのみ、またはメソッドの呼び出しでパラメーターとして渡すことがある場合は、このオプションを使用します。 型`londonCusts5`次の例では、IEnumerable (Of NamePhone)。  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 使用する方法についての詳細、 `Select` Visual basic での句を参照してください[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)です。  
  
## <a name="joining-data-join-and-group-join"></a>結合するデータ (結合と Group Join)  
 内の 1 つ以上のデータ ソースを組み合わせることができます、`From`方法はいくつかの句。 たとえば、次のコードでは、2 つのデータ ソースを使用して、結果に、これらの両方からのプロパティを暗黙的に結合します。 クエリでは、最後で始まる母音受講者を選択します。  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  作成した生徒数の一覧で、このコードを実行することができます[する方法: リストの項目を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)です。  
  
 `Join`キーワードは、 `INNER JOIN` SQL にします。 これは、2 つのコレクション内の要素間の一致するキー値に基づいて 2 つのコレクションを結合します。 クエリは、キーの値が一致するコレクションの要素のすべてまたは一部を返します。 たとえば、次のコードでは、以前の暗黙の結合のアクションが重複しています。  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join`同じように単一の階層コレクションにコレクションを結合、 `LEFT JOIN` SQL にします。 詳細については、次を参照してください。 [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)と[Group Join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)です。  
  
## <a name="grouping-data-group-by"></a>データのグループ化 (Group By)  
 追加することができます、`Group By`句、クエリ結果の要素の 1 つまたは複数のフィールドに従って要素をグループ化します。 たとえば、次のコードでは、クラス、年ごと受講者をグループ化します。  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 作成した生徒数のリストを使用してこのコードを実行するかどうかは[する方法: リストの項目を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)からの出力、`For Each`ステートメントは。  
  
 Year: Junior  
  
 Tucker、Michael  
  
 Garcia、Hugo  
  
 Garcia、宮部  
  
 Tucker、実現  
  
 Year: シニア  
  
 Omelchenko、Svetlana  
  
 田山、Michiko  
  
 Fakhouri、Fadi  
  
 Feng、Hanying  
  
 Terry Adams  
  
 Year: Freshman  
  
 Mortensen、Sven  
  
 Garcia、金  
  
 次のコードに示すように変化は、クラス年の注文し、最後の名前で各学年の受講者を並べ替えます。  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 詳細については`Group By`を参照してください[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
