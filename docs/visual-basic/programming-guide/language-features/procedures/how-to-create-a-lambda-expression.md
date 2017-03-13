---
title: "How to: Create a Lambda Expression (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "lambda expressions [Visual Basic]"
  - "expressions [Visual Basic], lambda"
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# How to: Create a Lambda Expression (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*ラムダ式*とは、名前を持たない関数またはサブルーチンです。  ラムダ式は、デリゲート型が有効な場所で使用できます。  
  
### 単一行のラムダ式関数を作成するには  
  
1.  デリゲート型を使用できる場所に、次の例に示すように、キーワード `Function` を入力します。  
  
     `Dim add1 =`   `Function`  
  
2.  `Function` の直後に、関数のパラメーターをかっこで囲んで入力します。  `Function` の後ろに名前を指定しないことに注意してください。  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  パラメーター リストの次に、関数の本体として、式を 1 つ入力します。  この式の評価値が、この関数によって返される値になります。  戻り値の型を指定するのに `As` 句は使用しません。  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     ラムダ式は、整数の引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  または、次の例のようにしても、同じ結果を得ることができます。  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### 単一行のラムダ式サブルーチンを作成するには  
  
1.  デリゲート型を使用できる場所に、次の例に示すように、キーワード `Sub` を入力します。  
  
     `Dim add1 =`   `Sub`  
  
2.  `Sub` の直後に、サブルーチンのパラメーターをかっこで囲んで入力します。  `Sub` の後ろに名前を指定しないことに注意してください。  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  パラメーター リストの次に、サブルーチンの本体として、ステートメントを 1 つ入力します。  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     ラムダ式は、文字列の引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### 複数行のラムダ式関数を作成するには  
  
1.  デリゲート型を使用できる場所に、次の例に示すように、キーワード `Function` を入力します。  
  
     `Dim add1 =`   `Function`  
  
2.  `Function` の直後に、関数のパラメーターをかっこで囲んで入力します。  `Function` の後ろに名前を指定しないことに注意してください。  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Enter キーを押します。  `End Function` ステートメントが自動的に追加されます。  
  
4.  関数の本体に、式を作成して値を返すための次のコードを追加します。  戻り値の型を指定するのに `As` 句は使用しません。  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     ラムダ式は、整数の引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### 複数行のラムダ式サブルーチンを作成するには  
  
1.  デリゲート型を使用できる場所に、次の例に示すように、キーワード `Sub` を入力します。  
  
     `Dim add1 =`   `Sub`  
  
2.  `Sub` の直後に、サブルーチンのパラメーターをかっこで囲んで入力します。  `Sub` の後ろに名前を指定しないことに注意してください。  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Enter キーを押します。  `End Sub` ステートメントが自動的に追加されます。  
  
4.  関数の本体に、サブルーチンが呼び出されたときに実行する次のコードを追加します。  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     ラムダ式は、文字列の引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## 使用例  
 ラムダ式の一般的な使用目的は、`Delegate` 型のパラメーターの引数として渡すことができる関数を定義することです。  次の例では、<xref:System.Diagnostics.Process.GetProcesses%2A> メソッドが、ローカル コンピューターで実行中のプロセスの配列を返します。  <xref:System.Linq.Enumerable> クラスの <xref:System.Linq.Enumerable.Where%2A> メソッドは、引数として `Boolean` デリゲートを必要とします。  この例では、その目的を果たすために、ラムダ式が使用されます。  ラムダ式は、スレッドが 1 つだけあるプロセスで、`filteredList` で選択されたプロセスごとに、`True` を返します。  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 前のコード例は、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] 構文で記述された次のコードに相当します。  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## 参照  
 <xref:System.Linq.Enumerable>   
 [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)