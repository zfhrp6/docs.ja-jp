---
title: "From Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryFrom"
  - "vb.QueryFromIn"
  - "vb.QueryFromLet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], From"
  - "From clause"
  - "From statement"
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# From Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クエリに 1 つ以上の範囲変数とコレクションを指定します。  
  
## 構文  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`element`|必ず指定します。  コレクションの要素を反復処理するために使用する*範囲変数*。  範囲変数を使用して、クエリで `collection` を反復処理するときに、`collection` の各メンバーを参照します。  列挙型にする必要があります。|  
|`type`|省略可能です。  `element` の型。  `type` の指定がない場合、`element` の型は `collection` から推論されます。|  
|`collection`|必ず指定します。  クエリの対象となるコレクションを示します。  列挙型にする必要があります。|  
  
## 解説  
 `From` 句を使用して、クエリのソース データと、ソース コレクションの要素を参照するために使用する変数を識別します。  これらの変数を*範囲変数*と呼びます。  `Aggregate` 句を使用して集計結果だけを返すクエリを指定する場合を除いて、`From` 句は、クエリでは必須です。  詳細については、「[Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)」を参照してください。  
  
 1 つのクエリに複数の `From` 句を指定して、結合する複数のコレクションを指定できます。  複数のコレクションを指定した場合、各コレクションは別々に反復処理されます。コレクションに関連性がある場合は、結合することもできます。  コレクションの結合は、`Select` 句を使用して暗黙的に実行するか、`Join` 句または `Group Join` 句を使用して明示的に実行できます。  または、1 つの `From` 句の中に、関連性のある範囲変数とコレクションをコンマで区切ることで、複数の範囲変数とコレクションを指定できます。  次のコード例では、`From` 句の両方の構文のオプションを示しています。  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#21)]  
  
 `From` 句は、クエリのスコープを定義します。これは `For` ループのスコープに似ています。  したがって、クエリのスコープ内の各 `element` 範囲変数は一意の名前を持っている必要があります。  1 つのクエリに複数の `From` 句を指定できるので、後続の `From` 句で `From` 句の範囲変数を参照したり、直前の `From` 句の範囲変数を参照したりできます。  たとえば、次の例は、入れ子になった `From` 句を示しています。ここでは、2 番目の句のコレクションは、最初の句の範囲変数のプロパティに基づいています。  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#22)]  
  
 各 `From` 句の直後に別のクエリ句を任意に組み合わせて追加することで、クエリを絞り込むことができます。  クエリは、次の方法で絞り込むことができます。  
  
-   複数のコレクションを、`From` 句と `Select` 句を使用して暗黙的に結合する。または、`Join` 句または `Group Join` 句を使用して明示的に結合する。  
  
-   `Where` 句を使用して、クエリ結果をフィルター処理する。  
  
-   `Order By` 句を使用して、結果を並べ替える。  
  
-   `Group By` 句を使用して、類似する結果をグループ化する。  
  
-   `Aggregate` 句を使用して、クエリ結果全体を評価する集計関数を指定する。  
  
-   `Let` 句を使用して、コレクションの代わりに式によって値が決定される反復変数を使用する。  
  
-   `Distinct` 句を使用して、重複するクエリ結果を無視する。  
  
-   `Skip`、`Take`、`Skip While`、および `Take While` の各句を使用して、返される結果の一部を指定する。  
  
## 使用例  
 次のクエリ式では、`From` 句を使用して、`customers` コレクション内の各 `Customer` オブジェクト用の範囲変数 `cust` を宣言します。  `Where` 句は、この範囲変数を使用して、出力を指定された地区の顧客に制限します。  `For Each` ループにより、クエリ結果内の各顧客の会社名が表示されます。  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#23)]  
  
## 参照  
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Distinct Clause](../../../visual-basic/language-reference/queries/distinct-clause.md)   
 [Join Clause](../../../visual-basic/language-reference/queries/join-clause.md)   
 [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Let Clause](../../../visual-basic/language-reference/queries/let-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)