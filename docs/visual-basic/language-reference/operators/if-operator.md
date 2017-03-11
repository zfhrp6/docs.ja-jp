---
title: "If Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.IfOperator"
  - "IfOperator"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ternary operators"
  - "conditional execution"
  - "If expressions [Visual Basic]"
  - "conditional operator [Visual Basic]"
  - "If Operator [Visual Basic]"
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# If Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ショートサーキット評価を使用し、2 つの値の 1 つを選択して返します。  `If` 演算子は、3 つまたは 2 つの引数を指定して呼び出すことができます。  
  
## 構文  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## 3 引数での If 演算子の呼び出し  
 3 つの引数を使用して `If` を呼び出す場合、1 番目の引数は、`Boolean` としてキャストできる値に評価される必要があります。  この `Boolean` 値は、他の 2 つの引数のどちらを評価して返すかを決定します。  次の一覧は、`If` 演算子を 3 つの引数で呼び出す場合のみに適用されます。  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`argument1`|必ず指定します。  `Boolean`.  他の引数のどちらを評価して返すかを決定します。|  
|`argument2`|必ず指定します。  `Object`.  `argument1` が `True` と評価される場合、この引数を評価して返します。|  
|`argument3`|必ず指定します。  `Object`.  `argument1` が `False` に評価または `argument1` が [なし](../../../visual-basic/language-reference/nothing.md)に評価する [Null 許容](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` 変数の場合、と評価され、終了しました。|  
  
 3 つの引数で呼び出される `If` 演算子は `IIf` 関数と同じように機能しますが、ショートサーキット評価を使用する点が異なります。  `IIf` 関数は常に 3 つの引数すべてを評価しますが、3 つの引数の `If` 演算子が評価する引数は 2 つのみです。  1 番目の `If` 引数が評価され、結果が `Boolean` 値つまり `True` または `False` としてキャストされます。  値が `True` の場合、`argument2` は評価されて値が返されますが、`argument3` は評価されません。  `Boolean` 式の値が `False` の場合は、`argument3` が評価されて値が返され、`argument2` は評価されません。  3 つの引数で `If` を使用した場合の例を次に示します。  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/if-operator_1.vb)]  
  
 次の例では、ショートサーキット評価の値を示します。  この例では、`divisor` がゼロでない場合は、変数 `number` を変数 `divisor` で 2 回割ります。  ゼロの場合は、ランタイム エラーになるので、0 を返し、除算は行いません。  `If` 式はショートサーキット評価を使用するので、1 番目の引数の値に基づいて、2 番目または 3 番目の引数を評価します。  1 番目の引数が true の場合は、序数はゼロではなく、2 番目の引数を評価して除算を実行しても安全です。  1 番目の引数が false の場合は、3 番目の引数のみが評価され、0 が返されます。  したがって、序数が 0 の場合は、除算は実行されず、エラーは発生しません。  一方、`IIf` はショートサーキット評価を使用しないので、1 番目の引数が false であっても、2 番目の引数が評価されます。  このため、ゼロによる除算のランタイム エラーが発生します。  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/if-operator_2.vb)]  
  
## 2 引数での If 演算子の呼び出し  
 `If` の 1 番目の引数は省略できます。  したがって、2 つの引数のみで演算子を呼び出すことができます。  次の一覧は、`If` 演算子を 2 つの引数で呼び出す場合のみに適用されます。  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`argument2`|必ず指定します。  `Object`.  参照型または null 許容型を指定する必要があります。  `Nothing` 以外として評価される場合、この引数を評価して返します。|  
|`argument3`|必ず指定します。  `Object`.  `argument2` が `Nothing` と評価される場合、この引数を評価して返します。|  
  
 `Boolean` 引数を省略するときは、1 番目の引数に参照型または null 許容型を指定する必要があります。  1 番目の引数が `Nothing` と評価されると、2 番目の引数の値が返されます。  それ以外のすべての場合は、1 番目の引数の値が返されます。  次の例は、この評価がどのように動作するのかを示します。  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/if-operator_3.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Nothing](../../../visual-basic/language-reference/nothing.md)