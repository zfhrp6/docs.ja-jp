---
title: "ラムダ式 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.LambdaFunction
dev_langs:
- VB
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e50593e76afecfe8807c3cb5bac479245d2feaef
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="lambda-expressions-visual-basic"></a>ラムダ式 (Visual Basic)
A*ラムダ式*関数またはサブルーチン デリゲートが有効な場所で使用できる名前のないです。 ラムダ式は、関数またはサブルーチンを指定でき、単一行または複数行を指定できます。 ラムダ式に現在のスコープから値を渡すことができます。  
  
> [!NOTE]
>  `RemoveHandler`ステートメントは例外です。 デリゲート パラメーターのラムダ式を渡すことはできません`RemoveHandler`します。  
  
 ラムダ式を使用して作成する、`Function`または`Sub`キーワード、標準的な関数またはサブルーチンを作成すると同じです。 ただし、ステートメントでラムダ式が含まれています。  
  
 次の例は、ラムダ式を引数をインクリメントし、値を返します。 この例では、単一行と複数行のラムダ式の両方の構文、関数を示します。  
  
 [!code-vb[VbVbalrLambdas&#14;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 次の例は、値をコンソールに出力するラムダ式です。 この例では、単一行と複数行のラムダ式の両方の構文、サブルーチンを示します。  
  
 [!code-vb[VbVbalrLambdas&#15;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 前の例では変数名にラムダ式が割り当てられたことを確認します。 変数を参照するには、ラムダ式を呼び出します。 宣言し、次の例で示すように、同時に、ラムダ式を呼び出すことができます。  
  
 [!code-vb[VbVbalrLambdas&#3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 ラムダ式は関数呼び出しの結果値として返されることができます (例で示すように、[コンテキスト](#context)このトピックで後述する「)、するやに渡す引数としてデリゲート型を受け取るパラメーターが次の例で示すようにします。  
  
 [!code-vb[VbVbalrLambdas&#8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>ラムダ式の構文  
 ラムダ式の構文では、標準の関数またはサブルーチンに似ています。 相違点は次のとおりです。  
  
-   ラムダ式には、名前がありません。  
  
-   ラムダ式がなど、修飾子を持つことはできません`Overloads`または`Overrides`です。  
  
-   単一行のラムダ関数は使用しないでください、`As`戻り値の型を指定する句。 代わりに、型は、ラムダ式の本体に評価される値から推論されます。 たとえば、ラムダ式の本体は`cust.City = "London"`、戻り値の型`Boolean`します。  
  
-   複数行ラムダの関数のいずれかを指定できます戻り値の型を使用して、`As`句、または省略、`As`句戻り値の型を推論できるようにします。 ときに、`As`複数行のラムダ関数の句を省略すると、すべての主要な型である戻り値の型を推論、`Return`複数行のラムダ関数内のステートメントです。 *基準となる型*は一意の型に拡大変換できるその他のすべての種類です。 この一意の型を特定できない場合に絞り込むことが、配列内の他のすべての型の一意の型は、基準となる型。 これらの一意の型をどちらも特定できない場合は、`Object` が最も優先度の高い型になります。 この場合は場合、`Option Strict`に設定されている`On`、コンパイラ エラーが発生します。  
  
     式が指定された場合など、`Return`ステートメントは、型の値を含む`Integer`、 `Long`、および`Double`、結果の配列の型は`Double`です。 両方とも`Integer`と`Long`に拡大変換`Double`およびのみ`Double`します。 そのため、 `Double` が最も優先度の高い型になります。 詳細については、次を参照してください。[拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)します。  
  
-   単一行の関数の本文には、ステートメントではなく、値を返す式を指定する必要があります。 ない`Return`関数の単一行のステートメントです。 単一行の関数によって返される値は、関数の本体での式の値です。  
  
-   単一行のサブルーチンの本文は、単一行のステートメントである必要があります。  
  
-   単一行の関数やサブルーチンを含めていない、`End Function`または`End Sub`ステートメントです。  
  
-   ラムダ式のパラメーターのデータ型を指定するにを使用して、`As`キーワード、またはパラメーターのデータ型を推論することができます。 データ型、またはすべてを推論する必要がありますかすべてパラメーターが指定する必要があります。  
  
-   `Optional``Paramarray`パラメーターは使用できません。  
  
-   ジェネリック パラメーターを指定することはできません。  
  
## <a name="async-lambdas"></a>非同期ラムダ  
 ラムダ式およびステートメントを使用して非同期処理を組み込んでいるを簡単に作成することができます、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)と[Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)キーワードです。 たとえば、次に示す Windows フォーム例には、非同期メソッド `ExampleMethodAsync`を呼び出して待機するイベント ハンドラーが含まれています。  
  
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
  
 非同期ラムダを使用して、同じイベント ハンドラーを追加することができます、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)します。 次の例に示すように、このハンドラーを追加するには、ラムダ パラメーター リストの前に `Async` 修飾子を追加します。  
  
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
  
 作成して、非同期のメソッドを使用する方法の詳細については、次を参照してください。 [Async および Await を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)します。  
  
##  <a name="context"></a>コンテキスト  
 ラムダ式が定義されているスコープとコンテキストを共有します。 コンテナーのスコープ内に記述されたコードと同じアクセス権を持ちます。 これにより、メンバー変数、関数とサブへのアクセスが含まれます。 `Me`、コンテナーのスコープ内のローカル変数やパラメーター。  
  
 ローカル変数と、コンテナー スコープ内のパラメーターへのアクセスは、そのスコープの有効期間を超えて拡張できます。 ラムダ式を参照するデリゲートがガベージ コレクションを使用できない限り、元の環境変数へのアクセスは保持されます。 次の例で、変数`target`に対してローカルな`makeTheGame`、するメソッドは、ラムダ式`playTheGame`が定義されています。 返されたラムダ式が割り当てられている注`takeAGuess`で`Main`、ローカル変数にアクセスするにはまだ`target`です。  
  
 [!code-vb[VbVbalrLambdas&#12;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 次の例では、入れ子になったラムダ式のアクセス権は幅広いを示します。 返されたラムダ式の実行時に`Main`として`aDel`、これらの要素にアクセスします。  
  
-   定義されているクラスのフィールド:`aField`  
  
-   定義されているクラスのプロパティ:`aProp`  
  
-   メソッドのパラメーターの`functionWithNestedLambda`、それが定義されています。`level1`  
  
-   ローカル変数`functionWithNestedLambda`:`localVar`  
  
-   入れ子になったラムダ式のパラメーター:`level2`  
  
 [!code-vb[VbVbalrLambdas&#9;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>デリゲート型に変換します。  
 ラムダ式は、互換性のあるデリゲート型に暗黙的に変換できます。 互換性のための一般的な要件については、次を参照してください。[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。 たとえば、次のコード例に暗黙的に変換するラムダ式を示しています。`Func(Of Integer, Boolean)`またはデリゲート シグネチャの一致します。  
  
 [!code-vb[VbVbalrLambdas&#16;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 次のコード例は、暗黙的に変換するラムダ式を示しています。`Sub(Of Double, String, Double)`またはデリゲート シグネチャの一致します。  
  
 [!code-vb[VbVbalrLambdas 第&23;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 ラムダ式をデリゲートに割り当てるかをプロシージャに引数として渡すときに、パラメーター名を指定ができる型がデリゲートから取得されるようにすること、データ型を省略できます。  
  
## <a name="examples"></a>例  
  
-   次の例を返すラムダ式を定義する`True`場合 null 許容型の引数は、割り当てられた値と`False`場合はその値は`Nothing`です。  
  
     [!code-vb[VbVbalrLambdas&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   次の例では、配列内の最後の要素のインデックスを返すラムダ式を定義します。  
  
     [!code-vb[VbVbalrLambdas&#5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [方法: Visual Basic での別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [方法: ラムダ式を作成します。](./how-to-create-a-lambda-expression.md)   
 [厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)

