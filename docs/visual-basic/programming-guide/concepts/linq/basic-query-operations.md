---
title: "基本的なクエリ操作 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 37
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 87ff9173b5ff72385c8ecdc3ff13735e7be2a21d
ms.lasthandoff: 03/13/2017

---
# <a name="basic-query-operations-visual-basic"></a>基本的なクエリ操作 (Visual Basic)
このトピックでは、概要を[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]Visual Basic、およびクエリで実行される演算の一般的な種類の式。 詳細については、次のトピックを参照してください。  
  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [チュートリアル: Visual Basic でのクエリの作成](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>(From) データ ソースを指定します。  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリでは、まず、クエリを実行するデータ ソースを指定します。 したがって、`From`クエリ内の句は常に最初にします。 クエリ演算子は、選択し、ソースの種類に基づく結果を形成します。  
  
 [!code-vb[VbLINQBasicOps&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 `From`句データ ソースを指定`customers`、および*範囲変数*、`cust`です。 範囲変数ですが、ループの反復変数のように、クエリ式で実際の反復は行われません。 ときに、クエリを実行する多くの場合を使用して、`For Each`ループ、連続する各要素への参照として範囲変数`customers`します。 コンパイラの型を推論できるため`cust`、明示的に指定する必要はありません。 明示的な型指定の有無に記述されたクエリの例については、次を参照してください。[クエリ操作 (Visual Basic) での型の関係](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)します。  
  
 使用する方法の詳細についての`From`Visual basic での句を参照してください[From 句](../../../../visual-basic/language-reference/queries/from-clause.md)します。  
  
## <a name="filtering-data-where"></a>データのフィルター処理 (場所)  
 可能性があります、最も一般的なクエリ操作には、ブール式の形式でフィルターが適用しています。 クエリは、式が true の要素のみを返します。 A`Where`句を使用して、フィルター処理を実行します。 フィルターは、結果のシーケンスに含めるデータ ソース内のどの要素を指定します。 次の例では、ロンドンにあるアドレスを持っている顧客のみが含まれます。  
  
 [!code-vb[VbLINQBasicOps&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 などの論理演算子を使用する`And`と`Or`でフィルター式を組み合わせて、`Where`句。 たとえば、ロンドン、およびメンバー名が Devon 顧客のみを返すには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 ロンドンまたはパリにある顧客を取得するには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 使用する方法の詳細についての`Where`Visual basic での句を参照してください[Where 句の](../../../../visual-basic/language-reference/queries/where-clause.md)です。  
  
## <a name="ordering-data-order-by"></a>データ (Order By) の並べ替え  
 多くの場合は、特定の順序に返されるデータを並べ替えると便利なです。 `Order By`句が指定されたフィールドでソートされた、返されるシーケンスの要素を発生します。 たとえば、次のクエリがに基づいて結果を並べ替えます、`Name`プロパティです。 `Name`文字列では、a ~ Z、返されるデータは、アルファベット順に並べ替えられます。  
  
 [!code-vb[VbLINQBasicOps&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 Z から A、逆の順序で結果の順序を使用して、`Order By...Descending`句。 既定値は`Ascending`がいずれも`Ascending`も`Descending`を指定します。  
  
 使用する方法の詳細についての`Order By`Visual basic での句を参照してください[Order By 句](../../../../visual-basic/language-reference/queries/order-by-clause.md)します。  
  
## <a name="selecting-data-select"></a>データ (Select) を選択します。  
 `Select`句は、フォームと返される要素の内容を指定します。 完全な結果がで構成されているかどうかを指定するたとえば、`Customer`オブジェクト、1 つにすぎません`Customer`計算に基づいて、プロパティ、プロパティのサブセット、さまざまなデータ ソース、または新しい結果の種類からのプロパティの組み合わせ。 ときに、`Select`句がソース要素のコピー以外のものを発生した場合、操作が呼び出される、*投影*します。  
  
 完全なので構成されるコレクションを取得する`Customer`オブジェクトを範囲変数自体を選択します。  
  
 [!code-vb[VbLINQBasicOps&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 場合、`Customer`インスタンスは、多くのフィールドを持つ大きいオブジェクトと名前を取得することだけが、選択できるように`cust.Name`の次の例に示すようにします。 ローカル型推論のコレクションから結果の型が変更される`Customer`オブジェクトを文字列のコレクション。  
  
 [!code-vb[VbLINQBasicOps&#5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 データ ソースから複数のフィールドを選択するには、2 つの選択肢があります。  
  
-   `Select`句、結果に含めるフィールドを指定します。 コンパイラは、プロパティとしてこれらのフィールドを持つ匿名型を定義します。 詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。  
  
     次の例で返される要素は、匿名型のインスタンスであるためにことはできません参照する型名で別の場所で、コード内。 型のコンパイラが指定の名前には、通常の Visual Basic コードでは無効な文字が含まれています。 次の例のクエリによって返されるコレクション内の要素で`londonCusts4`匿名型のインスタンス  
  
     [!code-vb[VbLINQBasicOps&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     または  
  
-   結果に含めるを作成し、型のインスタンスを初期化する特定のフィールドを含む名前付きの型を定義、`Select`句。 これらは、返されますが、コレクションの外部の個別の結果を使用している場合にのみ、またはメソッドの呼び出しでパラメーターとして渡すことがある場合は、このオプションを使用します。 型`londonCusts5`次の例では、IEnumerable (Of NamePhone)。  
  
     [!code-vb[VbLINQBasicOps&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps&#8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 使用する方法の詳細についての`Select`Visual basic での句を参照してください[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)します。  
  
## <a name="joining-data-join-and-group-join"></a>結合のデータ (結合と Group Join)  
 1 つ以上のデータ ソースを組み合わせることができます、`From`方法はいくつかの句。 たとえば、次のコードでは、2 つのデータ ソースを使用して、結果に、これらの両方からのプロパティを暗黙的に結合します。 クエリでは、姓が母音で始まる受講者を選択します。  
  
 [!code-vb[VbLINQBasicOps&#9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  作成した学生の一覧にこのコードを実行する[方法: 項目の一覧を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)します。  
  
 `Join`キーワードは、 `INNER JOIN` sql です。 これは、2 つのコレクション内の要素間の一致するキー値に基づいて&2; つのコレクションを結合します。 このクエリは、キーの値が一致するコレクションの要素のすべてまたは一部を返します。 たとえば、次のコードでは、前の暗黙的な結合の操作が重複しています。  
  
 [!code-vb[VbLINQBasicOps&#10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join`同じように単一の階層コレクションにコレクションを結合、 `LEFT JOIN` sql です。 詳細については、次を参照してください。 [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)と[Group Join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)します。  
  
## <a name="grouping-data-group-by"></a>データのグループ化 (グループ化)  
 追加することができます、`Group By`句、クエリ結果の要素の&1; つまたは複数のフィールドに従って要素をグループ化します。 たとえば、次のコードでは、クラス、年ごと受講者をグループ化します。  
  
 [!code-vb[VbLINQBasicOps&#11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 作成した生徒のリストを使用してこのコードを実行するかどうかは[する方法: 項目の一覧を作成する](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)からの出力、`For Each`ステートメントは。  
  
 年: Junior  
  
 Tucker、Michael  
  
 Garcia、Hugo  
  
 Garcia Debra  
  
 Tucker Lance  
  
 年: シニア  
  
 Omelchenko Svetlana  
  
 田山 Michiko  
  
 Fakhouri Fadi  
  
 Hanying Feng  
  
 Terry Adams  
  
 年: Freshman  
  
 Mortensen Sven  
  
 Garcia Cesar  
  
 次のコードに示すように変化は、クラス年を注文し、各学年の姓の順、受講者を並べ替えます。  
  
 [!code-vb[VbLINQBasicOps&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 詳細については`Group By`を参照してください[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
