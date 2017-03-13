---
title: "Sub Expression (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
helpviewer_keywords: 
  - "lambda expressions [Visual Basic], sub expression"
  - "Sub Expression [Visual Basic]"
  - "subroutines [Visual Basic], sub expressions"
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Sub Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

サブルーチンとしてのラムダ式を定義するパラメーターおよびコードを宣言します。  
  
## 構文  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`parameterlist`|省略可能です。  プロシージャのパラメータを表すローカル変数名のリストです。  リストが空の場合もパラメーターが必要です。  詳細については、「[Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)」を参照してください。|  
|`statement`|必ず指定します。  単一のステートメントです。|  
|`statements`|必ず指定します。  ステートメントのリストです。|  
  
## 解説  
 *ラムダ式*とは、名前を持たない、1 つ以上のステートメントを実行するサブルーチンです。  デリゲート型を使用できるすべての場所でラムダ式を使用できますが、`RemoveHandler` の引数としては使用できません。  デリゲートの詳細、およびデリゲートを含むラムダ式の使用については、「[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)」および「[Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)」を参照してください。  
  
## ラムダ式の構文  
 ラムダ式の構文は、標準のサブルーチンの構文に似ています。  相違点を次に示します。  
  
-   ラムダ式には名前がありません。  
  
-   ラムダ式では、`Overloads` や `Overrides` などの修飾子を使用できません。  
  
-   単一行のラムダ式の本体は、式ではなくステートメントである必要があります。  本体をサブ プロシージャへの呼び出しで構成することはできますが、関数プロシージャへの呼び出しは指定できません。  
  
-   ラムダ式では、すべてのパラメーターは、データ型が指定されているか推論される必要があります。  
  
-   ラムダ式では、Optional パラメーターと `ParamArray` パラメーターは使用できません。  
  
-   ラムダ式では、ジェネリック パラメーターは使用できません。  
  
## 使用例  
 以下は、コンソールに値を書き込むラムダ式の例です。  この例では、ラムダ式サブルーチンの単一行と複数行の両方の構文を示しています。  その他の例については、「[Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## 参照  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)