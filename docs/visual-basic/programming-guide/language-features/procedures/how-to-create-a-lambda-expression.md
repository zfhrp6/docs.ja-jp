---
title: "方法: ラムダ式 (Visual Basic) を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5e105e87b1e63218f2c3c2204350257c139b5837
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>方法: ラムダ式を作成する (Visual Basic)
A*ラムダ式*関数またはサブルーチンに名前がないです。 ラムダ式は、デリゲート型が有効な場所で使用できます。  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>単一行のラムダ式の関数を作成するには  
  
1.  どのような状況にデリゲート型を使用できる場所で、キーワードを入力`Function`次の例のようにします。  
  
     `Dim add1 =`   `Function`  
  
2.  かっこで囲んで直後後`Function`関数のパラメーターを入力します。 後の名前を指定しないことに注意してください。`Function`します。  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  次のパラメーター リストには、関数の本体として&1; つの式を入力します。 式の評価結果の値は、関数によって返される値です。 使用しない、`As`句を戻り値の型を指定します。  
  
     [!code-vb[VbVbalrLambdas&#1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     ラムダ式は、整数の引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas&#2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  また、同じ結果は、次の例で行われます。  
  
     [!code-vb[VbVbalrLambdas&#3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>単一行のラムダ式のサブルーチンを作成するには  
  
1.  デリゲート型を使用できる場所の状況で、キーワードを入力`Sub`の次の例に示すようにします。  
  
     `Dim add1 =`   `Sub`  
  
2.  かっこで囲んで直後後`Sub`サブルーチンのパラメーターを入力します。 後の名前を指定しないことに注意してください。`Sub`します。  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  次のパラメーター リストには、サブルーチンの本文として&1; つのステートメントを入力します。  
  
     [!code-vb[VbVbalrLambdas&17;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     ラムダ式は、文字列引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas&#18;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>複数行のラムダ式の関数を作成するには  
  
1.  デリゲート型を使用できる場所の状況で、キーワードを入力`Function`の次の例に示すようにします。  
  
     `Dim add1 =`   `Function`  
  
2.  かっこで囲んで直後後`Function`関数のパラメーターを入力します。 後の名前を指定しないことに注意してください。`Function`します。  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  ENTER キーを押します。 `End Function`ステートメントが自動的に追加します。  
  
4.  関数の本体内で式を作成し、値を返すには、次のコードを追加します。 使用しない、`As`句を戻り値の型を指定します。  
  
     [!code-vb[VbVbalrLambdas&#19;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     ラムダ式は、整数の引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas&#20;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>複数行のラムダ式のサブルーチンを作成するには  
  
1.  どのような状況にデリゲート型を使用できる場所で、キーワードを入力`Sub`次の例のように。  
  
     `Dim add1 =`   `Sub`  
  
2.  かっこで囲んで直後後`Sub`サブルーチンのパラメーターを入力します。 後の名前を指定しないことに注意してください。`Sub`します。  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  ENTER キーを押します。 `End Sub`ステートメントが自動的に追加します。  
  
4.  関数の本体内で、サブルーチンが呼び出されたときに実行する次のコードを追加します。  
  
     [!code-vb[VbVbalrLambdas #&21;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     ラムダ式は、文字列引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas #&22;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>例  
 型を持つパラメーターの引数として渡すことができる関数を定義するラムダ式の一般的な用途は、`Delegate`です。 次の例では、<xref:System.Diagnostics.Process.GetProcesses%2A>メソッドは、ローカル コンピューター上で実行されるプロセスの配列を返します</xref:System.Diagnostics.Process.GetProcesses%2A>。 <xref:System.Linq.Enumerable.Where%2A>からメソッド、<xref:System.Linq.Enumerable>クラスを必要とする`Boolean`デリゲートの引数として</xref:System.Linq.Enumerable></xref:System.Linq.Enumerable.Where%2A>。 ラムダ式の例では、その目的に使用されます。 返す`True`の各プロセスのスレッドが&1; つだけありで選択されている`filteredList`します。  
  
 [!code-vb[VbVbalrLambdas&#10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 前の例は次のコードで記述された[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]構文。  
  
 [!code-vb[VbVbalrLambdas&#11;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [ラムダ式](./lambda-expressions.md)   
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [方法: Visual Basic での別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
