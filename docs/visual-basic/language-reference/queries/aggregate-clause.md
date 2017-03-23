---
title: "Aggregate Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryAggregateIn"
  - "vb.QueryAggregate"
  - "vb.QueryAggregateInto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Aggregate clause"
  - "Aggregate statement"
  - "queries [Visual Basic], Aggregate"
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Aggregate Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

1 つ以上の集計関数をコレクションに適用します。  
  
## 構文  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`element`|必ず指定します。  コレクションの各要素を反復処理するために使用する変数。|  
|`type`|省略可能です。  `element` の型。  型の指定がない場合、`element` の型は `collection` から推論されます。|  
|`collection`|必ず指定します。  操作対象のコレクションを参照します。|  
|`clause`|省略可能です。  クエリ結果を絞り込むために集計句に適用する、`Where` 句などの 1 つ以上のクエリ句。|  
|`expressionList`|必ず指定します。  コレクションに適用する集計関数を識別する、1 つまたは複数のコンマで区切られた式。  集計関数にエイリアスを適用して、クエリ結果のメンバー名を指定できます。  エイリアスの指定がない場合は、集計関数の名前が使用されます。  例については、後の集計関数に関するセクションを参照してください。|  
  
## 解説  
 `Aggregate` 句を使用すると、クエリに集計関数を含めることができます。  集計関数は、一連の値のチェックと計算を実行し、単一の値を返します。  クエリ結果型のメンバーを使用することで、計算後の値にアクセスできます。  使用できる標準的な集計関数には、`All`、`Any`、`Average`、`Count`、`LongCount`、`Max`、`Min`、および `Sum` の各関数があります。  これらの関数は、SQL での集計に精通している開発者にとってはなじみのあるものです。  これらについては、このトピックの次のセクションで説明します。  
  
 集計関数の結果は、クエリ結果の中にクエリ結果型のフィールドとして格納されます。  集計関数の結果にエイリアスを適用して、集計値を保持するクエリ結果型のメンバーの名前を指定できます。  エイリアスの指定がない場合は、集計関数の名前が使用されます。  
  
 `Aggregate` 句は、クエリを開始することも、クエリ内に追加の句として含めることもできます。  `Aggregate` 句でクエリを開始した場合、結果は、`Into` 句に指定された集計関数の結果と同じ単一の値になります。  `Into` 句に複数の集計関数を指定した場合は、クエリから、`Into` 句に含まれる集計関数のそれぞれの結果を参照する個別のプロパティを持つ単一の型が返されます。  `Aggregate` 句がクエリ内の追加の句として指定された場合、クエリのコレクションに返される型は、`Into` 句に指定された集計関数のそれぞれの結果を参照する個別のプロパティを持ちます。  
  
## 集計関数  
 `Aggregate` 句と共に使用できる標準的な集計関数を次に示します。  
  
|||  
|-|-|  
|Function|Description|  
|`All`|コレクション内のすべての要素が、指定された条件を満たす場合は `true` を返します。それ以外の場合は `false` を返します。  例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|コレクション内のいずれかの要素が、指定された条件を満たす場合は `true` を返します。それ以外の場合は `false` を返します。  例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|コレクション内のすべての要素の平均を計算します。または、コレクション内のすべての要素に対して、指定された式を計算します。  例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|コレクション内の要素の数をカウントします。  オプションの `Boolean` 式を指定することで、コレクション内で条件を満たしている要素の数だけをカウントできます。  例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|`Group By` 句または `Group Join` 句の結果としてグループ化されているクエリ結果を参照します。  `Group` 関数は、`Group By` 句または `Group Join` 句の `Into` 句でのみ有効です。  使用例を含む詳細については、「[Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)」および「[Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)」を参照してください。|  
|`LongCount`|コレクション内の要素の数をカウントします。  オプションの `Boolean` 式を指定することで、コレクション内で条件を満たしている要素の数だけをカウントできます。  結果を `Long` として返します。  例については、`Count` 集計関数を参照してください。|  
|`Max`|コレクションの最大値を計算します。または、コレクション内のすべての要素に対して、指定された式を計算します。  例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|コレクションの最小値を計算します。または、コレクション内のすべての要素に対して、指定された式を計算します。  例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|コレクション内のすべての要素の合計を計算します。または、コレクション内のすべての要素に対して、指定された式を計算します。  例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## 使用例  
 次のコード例は、`Aggregate` 句を使用して集計関数をクエリ結果に適用する方法を示しています。  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## ユーザー定義集計関数の作成  
 <xref:System.Collections.Generic.IEnumerable%601> 型に拡張メソッドを追加することで、独自のカスタム集計関数をクエリ式の中に指定できます。  カスタム メソッドでは、その集計関数を参照した列挙可能なコレクションに対して計算または操作を実行できます。  拡張メソッドの詳細については、「[拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)」を参照してください。  
  
 たとえば、次のコード例は、数値コレクションの中央値を計算するカスタム集計関数を示します。  `Median` 拡張メソッドには 2 つのオーバーロードがあります。  最初のオーバーロードは、入力として `IEnumerable(Of Double)` 型のコレクションを受け取ります。  `Double` 型のクエリ フィールドに対して `Median` 集計関数が呼び出された場合は、このメソッドが呼び出されます。  `Median` メソッドの 2 番目のオーバーロードには、任意のジェネリック型を渡すことができます。  `Median` メソッドのジェネリック オーバーロードは、`Func(Of T, Double)` ラムダ式を参照する 2 番目のパラメーターを受け取り、コレクション内の型の値を対応する `Double` 型の値として投影するために使用します。  その後、中央値の計算を `Median` メソッドの他のオーバーロードに委任します。  ラムダ式の詳細については、「[Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 次のコード例は、`Integer` 型のコレクションと `Double` 型のコレクションに対して `Median` 集計関数を呼び出す例を示します。  `Double` 型のコレクションに対して `Median` 集計関数を呼び出すクエリでは、`Double` 型のコレクションを入力として受け取る `Median` メソッドのオーバーロードが呼び出されます。  `Integer` 型のコレクションに対して `Median` 集計関数を呼び出すクエリでは、`Median` メソッドのジェネリック オーバーロードが呼び出されます。  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)