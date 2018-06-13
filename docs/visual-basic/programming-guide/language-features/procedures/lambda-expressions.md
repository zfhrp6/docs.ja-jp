---
title: ラムダ式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c45500dc7a1e59a7ac83d43b826ca4cbfca6efb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654795"
---
# <a name="lambda-expressions-visual-basic"></a>ラムダ式 (Visual Basic)
A*ラムダ式*は関数またはサブルーチン デリゲートが有効な場所で使用できる名前のないです。 ラムダ式は関数またはサブルーチンを指定でき、単一行または複数行を指定できます。 ラムダ式に現在のスコープから値を渡すことができます。  
  
> [!NOTE]
>  `RemoveHandler`ステートメントは例外です。 デリゲート パラメーターのラムダ式を渡すことはできません`RemoveHandler`です。  
  
 ラムダ式を使用して作成する、`Function`または`Sub`キーワード、標準の関数またはサブルーチンを作成すると同様です。 ただし、ステートメントでは、ラムダ式が含まれます。  
  
 次の例は、ラムダ式をその引数をインクリメントし、値を返します。 この例では、単一行および複数行ラムダ式の両方の構文、関数を示します。  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 次の例は、値をコンソールに出力するラムダ式です。 この例では、単一行および複数行ラムダ式の両方の構文のサブルーチンを示します。  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 前の例で、ラムダ式に割り当てられている変数の名前に注意してください。 変数を参照するには、ラムダ式を呼び出します。 宣言し、次の例で示すように、同時に、ラムダ式を呼び出すことができます。  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 ラムダ式は関数呼び出しの結果値として返すことができます (例に示すように、[コンテキスト](#context)このトピックで後述する「)、に渡されるで引数としてデリゲート型を受け取るパラメーター次に示すように、または例です。  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>ラムダ式の構文  
 ラムダ式の構文では、標準の関数またはサブルーチンに似ています。 相違点は次のとおりです。  
  
-   ラムダ式には、名前がありません。  
  
-   ラムダ式ことも、修飾子など`Overloads`または`Overrides`です。  
  
-   単一行のラムダ関数は使用しないで、`As`戻り値の型を指定する句。 代わりに、型は、ラムダ式の本体に評価される値から推論されます。 たとえば、ラムダ式の本体が`cust.City = "London"`、戻り値の型は`Boolean`します。  
  
-   複数行ラムダ関数のいずれかを指定できます戻り値の型を使用して、`As`句、または省略、`As`句戻り値の型を推論できるようにします。 ときに、`As`複数行ラムダ関数の句を省略すると、すべての主要な型である戻り値の型を推論、`Return`複数行ラムダ関数内のステートメント。 *基準となる型*は一意の型に拡大変換できるその他のすべての型です。 この一意の型を特定できない場合に絞り込むことが、配列内の他のすべての型を一意の型は、主要な型です。 これらの一意の型をどちらも特定できない場合は、 `Object`が最も優先度の高い型になります。 この例では場合、`Option Strict`に設定されている`On`、コンパイラ エラーが発生します。  
  
     式が指定された場合など、`Return`ステートメントは、型の値を含む`Integer`、 `Long`、および`Double`、結果の配列の型は`Double`します。 両方`Integer`と`Long`に拡大変換`Double`とのみ`Double`です。 そのため、 `Double` が最も優先度の高い型になります。 詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
-   単一行の関数の本体は、ステートメントではなく、値を返す式である必要があります。 ない`Return`関数の単一行ステートメントです。 単一行の関数によって返される値は、関数の本体での式の値です。  
  
-   単一行のサブルーチンの本体では、単一行ステートメントを指定する必要があります。  
  
-   単一行関数やサブルーチンを含めていない、`End Function`または`End Sub`ステートメントです。  
  
-   ラムダ式のパラメーターのデータ型を使用して指定することができます、`As`キーワード、またはパラメーターのデータ型を推論することができます。 データ型またはすべてを推論する必要がありますかすべてのパラメーターが指定する必要があります。  
  
-   `Optional` `Paramarray`パラメーターは使用できません。  
  
-   ジェネリック パラメーターを指定することはできません。  
  
## <a name="async-lambdas"></a>非同期ラムダ  
 ラムダ式およびステートメントを使用して、非同期処理を組み込んだを簡単に作成することができます、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)と[Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)キーワード。 たとえば、次に示す Windows フォーム例には、非同期メソッド `ExampleMethodAsync`を呼び出して待機するイベント ハンドラーが含まれています。  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 非同期のラムダを使用して、同じイベント ハンドラーを追加することができます、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)です。 次の例に示すように、このハンドラーを追加するには、ラムダ パラメーター リストの前に `Async` 修飾子を追加します。  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 作成して、非同期メソッドを使用する方法の詳細については、次を参照してください。 [Async および Await を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)です。  
  
##  <a name="context"></a> コンテキスト  
 ラムダ式は、内部で定義されたスコープとコンテキストを共有します。 コンテナーのスコープで記述されたコードと同じアクセス権を持ちます。 メンバー変数、関数とサブへのアクセスが含まれます`Me`、コンテナーのスコープ内のローカル変数やパラメーター。  
  
 ローカル変数と、コンテナー スコープ内のパラメーターへのアクセスは、そのスコープの有効期間を超えて拡張できます。 ラムダ式を参照するデリゲートがガベージ コレクションを使用できない限り、元の環境変数へのアクセスは保持されます。 次の例で、変数`target`に対してローカルな`makeTheGame`をメソッド、ラムダ式`playTheGame`が定義されています。 返されたラムダ式が割り当てられている注`takeAGuess`で`Main`、引き続きローカル変数にアクセスしている`target`です。  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 次の例では、入れ子になったラムダ式のアクセス権の幅の広い範囲を示します。 返されたラムダ式を実行すると`Main`として`aDel`、これらの要素にアクセスします。  
  
-   定義されているクラスのフィールド: `aField`  
  
-   定義されているクラスのプロパティ: `aProp`  
  
-   メソッドのパラメーター `functionWithNestedLambda`、それが定義されています。 `level1`  
  
-   ローカル変数`functionWithNestedLambda`: `localVar`  
  
-   入れ子になったラムダ式のパラメーター: `level2`  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>デリゲート型に変換します。  
 ラムダ式は、互換性のあるデリゲート型に暗黙的に変換できます。 互換性のための一般的な要件については、次を参照してください。[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)です。 たとえば、次のコード例に暗黙的に変換するラムダ式を示しています。`Func(Of Integer, Boolean)`またはデリゲートのシグネチャが一致します。  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 次のコード例は、暗黙的に変換する、ラムダ式を示しています。`Sub(Of Double, String, Double)`またはデリゲートのシグネチャが一致します。  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 ラムダ式をデリゲートに割り当てるまたはプロシージャに引数として渡したりするときに、パラメーター名を指定は、データ型、型がデリゲートから取得されるを省略できます。  
  
## <a name="examples"></a>使用例  
  
-   次の例を返すラムダ式を定義する`True`null 許容型の引数に値が割り当てられる場合と`False`場合はその値は`Nothing`します。  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   次の例では、配列内の最後の要素のインデックスを返すラムダ式を定義します。  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 方法 : [Visual Basic でプロシージャを別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [方法 : ラムダ式を作成する](./how-to-create-a-lambda-expression.md)  
 [厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
