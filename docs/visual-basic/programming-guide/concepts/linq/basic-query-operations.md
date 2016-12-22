---
title: "基本的なクエリ操作 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "データ ソース [Visual Basic での LINQ]"
  - "Join 句 [Visual Basic での LINQ]"
  - "順序付け (データを) [Visual Basic での LINQ]"
  - "射影 [Visual Basic での LINQ]"
  - "LINQ [Visual Basic]、クエリ操作"
  - "Order By 句 [Visual Basic での LINQ]"
  - "結合 (データを) [Visual Basic での LINQ]"
  - "クエリ [Visual Basic での LINQ]、基本操作"
  - "選択 (データを) [Visual Basic での LINQ]"
  - "Group By 句 [Visual Basic での LINQ]"
  - "グループ化 (データを) [Visual Basic での LINQ]"
  - "Select 句 [Visual Basic での LINQ]"
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
caps.latest.revision: 37
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 基本的なクエリ操作 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

ここでは、Visual Basic における[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] 式と、クエリで実行する一般的な操作について簡単に紹介します。  詳細については、次のトピックを参照してください。  
  
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [チュートリアル: Visual Basic でクエリを記述する](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## データ ソースの指定 \(From\)  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリに必要な最初の手順は、照会するデータ ソースを指定することです。  したがって、クエリの `From` 句は常に最初に指定します。クエリ演算子は、ソースの種類に基づいて結果を選択および設定します。  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 この `From` 句では、データ ソース `customers` と*範囲変数* `cust` を指定しています。  範囲変数はループの反復変数に似ていますが、クエリ式で実際の反復が発生しない点が異なります。  通常、`For Each` ループを使用してクエリを実行すると、範囲変数は `customers` の連続する各要素への参照として機能します。  `cust` の型はコンパイラで推論できるので、明示的に指定する必要はありません。  明示的な型指定を使用して作成されたクエリと、使用せずに作成されたクエリの例については、「[Type Relationships in Query Operations \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)」を参照してください。  
  
 Visual Basic で `From` 句を使用する方法の詳細については、「[From Clause](../../../../visual-basic/language-reference/queries/from-clause.md)」を参照してください。  
  
## データのフィルター処理 \(Where\)  
 おそらく、最も一般的なクエリ操作は、ブール式の形式でフィルターを適用することです。  このようなクエリでは、式が true になる要素だけが返されます。  フィルター処理を実行するには、`Where` 句を使用します。  フィルターでは、結果のシーケンスに含めるデータ ソース内の要素を指定します。  住所がロンドンにある顧客だけを含める例を次に示します。  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 `Where` 句では、`And` や `Or` などの論理演算子を使用してフィルター式を結合できます。  たとえば、住所がロンドンで名前が Devon の顧客だけを返すには、次のコードを使用します。  
  
```vb#  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 住所がロンドンまたはパリにある顧客を返すには、次のコードを使用します。  
  
```vb#  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Visual Basic で `Where` 句を使用する方法の詳細については、「[Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md)」を参照してください。  
  
## データの順序付け \(Order By\)  
 返されるデータを特定の順序に並べ替えると便利な場合がよくあります。  `Order By` 句は、返されるシーケンス内の要素を、指定した 1 つまたは複数のフィールドの順に並べ替えます。  たとえば、次のクエリは `Name` プロパティに基づいて結果を並べ替えます。  `Name` は文字列なので、返されるデータはアルファベット順 \(A ～ Z\) に並べ替えられます。  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 結果を逆の順序 \(Z ～ A\) で並べ替えるには、`Order By...Descending` 句を使用します。  `Ascending` も `Descending` も指定しなかった場合の既定値は `Ascending` です。  
  
 Visual Basic で `Order By` 句を使用する方法の詳細については、「[Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
## データの選択 \(Select\)  
 `Select` 句は、返される要素の形式および内容を指定します。  たとえば、完全な `Customer` オブジェクト、1 つの `Customer` プロパティのみ、プロパティのサブセット、さまざまなデータ ソースからのプロパティの組み合わせ、計算に基づいた新しい結果の種類のいずれから結果が構成されるかを指定できます。  `Select` 句がソース要素のコピー以外を生成する場合、その操作は*投影*と呼ばれます。  
  
 完全な `Customer` オブジェクトで構成されるコレクションを取得するには、範囲変数自体を選択します。  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 `Customer` インスタンスが多数のフィールドを持つ大きいオブジェクトで、名前のみを取得すればよい場合は、次の例に示すように `cust.Name` を選択できます。  この場合、ローカル型の推論によって、結果の種類が `Customer` オブジェクトのコレクションから文字列のコレクションに変更されることが認識されます。  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 データ ソースから複数のフィールドを選択するには、次の 2 つの方法があります。  
  
-   `Select` 句で、結果に含める各フィールドを指定します。  コンパイラは、それらのフィールドをプロパティとして持つ匿名型を定義します。  詳細については、「[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
     次の例で返される要素は匿名型のインスタンスであるため、コード内で型を名前で参照することはできません。  コンパイラによって指定される型の名前には、通常の Visual Basic コードでは無効な文字が含まれます。  次の例では、`londonCusts4` のクエリが返すコレクション内の各要素は匿名型のインスタンスです。  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     または  
  
-   結果に含める特定のフィールドを格納する名前付きの型を定義し、`Select` 句で型のインスタンスを作成および初期化します。  この方法は、コレクション内に返された個々の結果を、そのコレクションの外部で使用する必要がある場合、またはメソッド呼び出しのパラメーターとして渡す必要がある場合にのみ使用します。  次の例では、`londonCusts5` の型は IEnumerable\(Of NamePhone\) になります。  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 Visual Basic で `Select` 句を使用する方法の詳細については、「[Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md)」を参照してください。  
  
## データの結合 \(Join および Group Join\)  
 `From` 句では、いくつかの方法で複数のデータ ソースを結合できます。  たとえば、次のコードは 2 つのデータ ソースを使用し、結果で両方のデータ ソースのプロパティを暗黙的に結合します。  このクエリは、姓が母音で始まる生徒を選択します。  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  「[How to: Create a List of Items](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md)」で作成した生徒のリストを使用して、このコードを実行できます。  
  
 `Join` キーワードは、SQL の `INNER JOIN` に相当します。  2 つのコレクション内の要素間で一致するキー値に基づいて、2 つのコレクションを結合します。  クエリは、一致するキー値を持つコレクション要素のすべてまたは一部を返します。  たとえば、次のコードは前の暗黙的な結合と同じ動作を実行します。  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join` は、SQL の `LEFT JOIN` と同じように、コレクションを 1 つの階層コレクションに結合します。  詳細については、「[Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md)」および「[Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md)」を参照してください。  
  
## データのグループ化 \(Group By\)  
 `Group By` 句を追加すると、要素の 1 つ以上のフィールドに従って、クエリ結果内の要素をグループ化できます。  たとえば、次のコードは生徒を学年別にグループ化します。  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 「[How to: Create a List of Items](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md)」で作成した生徒のリストを使用してこのコードを実行すると、`For Each` ステートメントの出力は次のようになります。  
  
 Year: Junior  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Year: Senior  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Year: Freshman  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 次のコードに示すバリエーションでは、学年を並べ替え、各学年の生徒を姓の順に並べ替えます。  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 `Group By` の詳細については、「[Group By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)」を参照してください。  
  
## 参照  
 <xref:System.Collections.Generic.IEnumerable%601>   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Basic LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)