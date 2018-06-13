---
title: '方法: ラムダ式を作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: f437166bc5206b4145d6508aa2131ec94d6eca95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653547"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>方法: ラムダ式を作成する (Visual Basic)
A*ラムダ式*は関数またはサブルーチンに名前がないです。 ラムダ式は、デリゲート型が有効な場所で使用できます。  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>単一行のラムダ式の関数を作成するには  
  
1.  どのような状況はデリゲート型を使用できる場所をキーワードを入力`Function`次の例のように、します。  
  
     `Dim add1 =`   `Function`  
  
2.  かっこ内のすぐ後に`Function`関数のパラメーターを入力します。 後に名前が指定されていないことに注意してください。`Function`です。  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  次のパラメーター リストには、関数の本体として 1 つの式を入力します。 式に評価される値は、関数によって返される値です。 使用しない、`As`句を戻り値の型を指定します。  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     ラムダ式は、整数の引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  代わりに、同じ結果には、次の例。  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>単一行のラムダ式のサブルーチンを作成するには  
  
1.  デリゲート型を使用できる場所の場合、キーワードを入力`Sub`の次の例に示すようにします。  
  
     `Dim add1 =`   `Sub`  
  
2.  かっこ内のすぐ後に`Sub`サブルーチンのパラメーターを入力します。 後に名前が指定されていないことに注意してください。`Sub`です。  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  次のパラメーター リストには、サブルーチンの本文として 1 つのステートメントを入力します。  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     ラムダ式は、文字列引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>複数行のラムダ式の関数を作成するには  
  
1.  デリゲート型を使用できる場所の場合、キーワードを入力`Function`の次の例に示すようにします。  
  
     `Dim add1 =`   `Function`  
  
2.  かっこ内のすぐ後に`Function`関数のパラメーターを入力します。 後に名前が指定されていないことに注意してください。`Function`です。  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  ENTER キーを押します。 `End Function`ステートメントが自動的に追加します。  
  
4.  関数の本体内では、式を作成して値を返すには、次のコードを追加します。 使用しない、`As`句を戻り値の型を指定します。  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     ラムダ式は、整数の引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>複数行のラムダ式のサブルーチンを作成するには  
  
1.  どのような状況はデリゲート型を使用できる場所をキーワードを入力`Sub`次の例のように。  
  
     `Dim add1 =`   `Sub`  
  
2.  かっこ内のすぐ後に`Sub`サブルーチンのパラメーターを入力します。 後に名前が指定されていないことに注意してください。`Sub`です。  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  ENTER キーを押します。 `End Sub`ステートメントが自動的に追加します。  
  
4.  関数の本体内では、サブルーチンが呼び出されるときに実行する次のコードを追加します。  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     ラムダ式は、文字列引数を渡すことによって呼び出します。  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>例  
 型を持つパラメーターの引数として渡すことができる関数を定義するラムダ式の一般的な用途は、`Delegate`です。 次の例で、<xref:System.Diagnostics.Process.GetProcesses%2A>メソッド、ローカル コンピューターで実行中のプロセスの配列を返します。 <xref:System.Linq.Enumerable.Where%2A>メソッドから、<xref:System.Linq.Enumerable>クラス必要があります、`Boolean`デリゲートの引数として。 ラムダ式の例では、そのような目的に使用されます。 返します`True`各プロセスのスレッドの 1 つだけ持ちで選択されている`filteredList`です。  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 前の例は、次のコードで記述された[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]構文。  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable>  
 [ラムダ式](./lambda-expressions.md)  
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 方法 : [Visual Basic でプロシージャを別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
