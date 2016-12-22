---
title: "Function Expression (Visual Basic) | Microsoft Docs"
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
  - "Function expression [Visual Basic]"
  - "functions [Visual Basic], function expressions"
  - "lambda expressions [Visual Basic], function expression"
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

関数としてのラムダ式を定義するパラメーターおよびコードを宣言します。  
  
## 構文  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`parameterlist`|省略可能です。  このプロシージャのパラメーターを表すローカル変数名のリスト。  リストが空の場合もパラメーターが必要です。  「[Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)」を参照してください。|  
|`expression`|必ず指定します。  1 つの式。  式の型は関数の戻り値の型です。|  
|`statements`|必ず指定します。  `Return` ステートメントを使用して値を返すステートメントの一覧です   \(「[Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)」を参照\)。返される値の型は、関数の戻り値の型です。|  
  
## 解説  
 *ラムダ式*とは、計算を実行して値を返す、名前を持たない関数です。  デリゲート型を使用できるすべての場所でラムダ式を使用できますが、`RemoveHandler` の引数としては使用できません。  デリゲートの詳細、およびデリゲートを含むラムダ式の使用については、「[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)」および「[Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)」を参照してください。  
  
## ラムダ式の構文  
 ラムダ式の構文は、標準関数の構文に似ています。  相違点を次に示します。  
  
-   ラムダ式には名前がありません。  
  
-   ラムダ式では、`Overloads` や `Overrides` などの修飾子を使用できません。  
  
-   ラムダ式では、`As` 句を使用して関数の戻り値の型を指定することはできません。  代わりに、単一行のラムダ式の本体を評価した値、または複数行のラムダ式の戻り値から型が推論されます。  たとえば、単一行のラムダ式の本体が `Where cust.City = "London"` の場合、その戻り値の型は `Boolean` になります。  
  
-   単一行のラムダ式の本体は、ステートメントではなく式である必要があります。  本体を関数プロシージャへの呼び出しで構成することはできますが、サブ プロシージャへの呼び出しは指定できません。  
  
-   すべてのパラメーターは、データ型が指定されているか推論される必要があります。  
  
-   Optional パラメーターと ParamArray パラメーターは使用できません。  
  
-   ジェネリック パラメーターは使用できません。  
  
## 使用例  
 単純なラムダ式を作成する 2 とおりの方法を次の例に示します。  最初の方法では、`Dim` を使用して関数の名前を提要します。  関数を呼び出すには、パラメーターの値を指定します。  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## 使用例  
 または、関数の宣言と実行を同時に行うことができます。  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## 使用例  
 以下は、引数をインクリメントし、その値を返すラムダ式の例です。  この例では、ラムダ式関数の単一行と複数行の両方の構文を示しています。  その他の例については、「[Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## 使用例  
 ラムダ式は、[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)] において多くのクエリ演算子の基礎になっており、メソッド ベースのクエリで明示的に使用できます。  次の例では、典型的な [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] クエリと、それに続いてクエリのメソッド形式への変換を示します。  
  
```vb#  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 クエリ メソッドの詳細については、「[Queries](../../../visual-basic/language-reference/queries/queries.md)」を参照してください。  標準クエリ演算子の詳細については、「[Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。  
  
## 参照  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Value Comparisons](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)