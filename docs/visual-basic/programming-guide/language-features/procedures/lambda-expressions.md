---
title: "Lambda Expressions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.LambdaFunction"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "functions [Visual Basic], lambda expressions"
  - "lambda expressions [Visual Basic]"
  - "expressions [Visual Basic], lambda"
  - "inline functions [Visual Basic]"
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 52
---
# Lambda Expressions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*ラムダ式*は、デリゲートが有効であれば使用できる、名前を持たない関数またはサブルーチンです。  ラムダ式は、単一行または複数行の関数またはサブルーチンとして作成できます。  ラムダ式には、現在のスコープから値を渡すことができます。  
  
> [!NOTE]
>  `RemoveHandler` ステートメントは例外です。  ラムダ式は、`RemoveHandler` のデリゲート パラメーターには渡せません。  
  
 ラムダ式は、標準の関数またはサブルーチンを作成する場合と同様に、`Function` キーワードまたは `Sub` キーワードを使用して作成できます。  ただし、ラムダ式はステートメント内に含まれます。  
  
 次の例は、引数をインクリメントし、その値を返すラムダ式を示します。  この例では、ラムダ式関数の単一行と複数行の両方の構文を示しています。  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 次の例は、コンソールに値を書き込むラムダ式です。  この例では、ラムダ式サブルーチンの単一行と複数行の両方の構文を示しています。  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 上記の例では、ラムダ式が変数名に割り当てられていることに注意してください。  この場合、変数を参照するたびにラムダ式を呼び出すことになります。  次の例に示すように、ラムダ式の宣言と呼び出しを同時に行うこともできます。  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 ラムダ式は、関数呼び出しの戻り値として返すことができます \(このトピックの「[コンテキスト](#context)」セクションに例が示されています\)。また、次の例に示すように、デリゲート型を受け取るパラメーターの引数として渡すこともできます。  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## ラムダ式の構文  
 ラムダ式の構文は、標準の関数やサブルーチンの構文に似ています。  相違点を次に示します。  
  
-   ラムダ式には名前がありません。  
  
-   ラムダ式では、`Overloads` や `Overrides` などの修飾子を使用できません。  
  
-   単一行のラムダ関数では、`As` 句を使用して戻り値の型を指定することはできません。  代わりに、ラムダ式の本体を評価した値から型が推論されます。  たとえば、ラムダ式の本体が `cust.City = "London"` の場合、その戻り値の型は `Boolean` になります。  
  
-   複数行のラムダ関数では、`As` 句を使用して戻り値の型を指定するか、`As` 句を省略して戻り値の型を推論することができます。  複数行のラムダ関数で `As` 句を省略した場合、戻り値の型は、複数行のラムダ関数のすべての `Return` ステートメントの中で最も優先度の高い型であると推論されます。  *主要な型*その他のすべてのタイプに広げることができますが一意の型します。  この一意の型を特定できない場合、最も優先度の高い型は、配列内の他のすべての型に縮小変換できる一意の型になります。  これらの一意の型をどちらも特定できない場合は、`Object` が最も優先度の高い型になります。  この場合、`Option Strict` が `On` に設定されていると、コンパイラ エラーになります。  
  
     式を指定する場合など、 `Return`ステートメントには、値型にはが含まれて`Integer`、 `Long`、および`Double`、結果の配列です`Double`。  `Integer` と `Long` はどちらも `Double` に拡大変換され、`Double` だけになります。  そのため、`Double` が最も優先度の高い型になります。  詳細については、「[Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
-   単一行の関数の本体は、ステートメントではなく、値を返す式である必要があります。  単一行の関数用の `Return` ステートメントはありません。  単一行の関数によって返される値は、関数の本体に指定された式の値です。  
  
-   単一行のサブルーチンの本体は、単一行のステートメントである必要があります。  
  
-   単一行の関数およびサブルーチンには、`End Function` ステートメントや `End Sub` ステートメントは含まれません。  
  
-   ラムダ式のパラメーターのデータ型は `As` キーワードを使用して指定するか、推論することができます。  すべてのパラメーターは、データ型が指定されているか推論される必要があります。  
  
-   `Optional` パラメーターと `Paramarray` パラメーターは使用できません。  
  
-   ジェネリック パラメーターは使用できません。  
  
## 非同期のラムダ  
 ラムダ式とステートメントを使用して非同期処理を組み込むことを簡単に作成することができます、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)と[Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md)キーワードします。  たとえば、次の Windows フォームの例を呼び出すし、非同期メソッドを待機するイベント ハンドラーが含まれている`ExampleMethodAsync`。  
  
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
  
 非同期ラムダを使用して、同じイベント ハンドラーを追加することができます、 [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。  このハンドラーを追加するには、追加、 `Async`修飾子はラムダ パラメーターのリストを次のようにします。  
  
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
  
 作成し、非同期のメソッドを使用する方法の詳細についてを参照してください[Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  
  
##  <a name="context"></a> コンテキスト  
 ラムダ式は、それが定義されている外側のスコープとコンテキストを共有します。  ラムダ式は、コンテナー スコープに記述されているすべてのコードと同じアクセス権を持ちます。  これには、コンテナー スコープ内のメンバー変数、関数、サブ関数、`Me`、パラメーター、およびローカル変数へのアクセスも含まれます。  
  
 コンテナー スコープ内のローカル変数とパラメーターは、そのスコープの有効期間以降もアクセスされる可能性があります。  ラムダ式を参照するデリゲートがガベージ コレクションの対象にならない限り、元の環境での変数へのアクセスは保持されます。  次の例では、変数 `target` は、ラムダ式 `playTheGame` が定義されているメソッド `makeTheGame` にローカルです。  返されたラムダ式は、`Main` で `takeAGuess` に割り当てられ、ローカル変数 `target` へのアクセスを保持し続けていることに注意してください。  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 次の例では、入れ子になったラムダ式の広範囲のアクセス権を示します。  返されたラムダ式は、`Main` から `aDel` として実行されるときに、これらの要素にアクセスします。  
  
-   ラムダ式が定義されるクラスのフィールド: `aField`  
  
-   ラムダ式が定義されるクラスのプロパティ: `aProp`  
  
-   ラムダ式が定義される `functionWithNestedLambda` メソッドのパラメーター: `level1`  
  
-   `functionWithNestedLambda` のローカル変数: `localVar`  
  
-   ラムダ式がネストされるラムダ式のパラメーター: `level2`  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## デリゲート型への変換  
 ラムダ式は、互換性のあるデリゲート式に明示的に変換できます。  互換性の一般的な要件については、「[Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)」を参照してください。  たとえば、次のコード例は、明示的に `Func(Of Integer, Boolean)` または対応するデリゲート シグネチャに変換するラムダ式を示しています。  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 次のコード例は、暗黙的に `Sub(Of Double, String, Double)` または対応するデリゲート シグネチャに変換するラムダ式を示しています。  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 ラムダ式をデリゲートに割り当てるときやプロシージャに引数として渡すときは、パラメーター名を指定してデータ型を省略することで、デリゲートから型が取得されるようにできます。  
  
## 例  
  
-   次の例は、null 許容引数に値が割り当てられた場合は `True` を返し、値が `Nothing` の場合は `False` を返すラムダ式を定義します。  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   次の例は、配列内の最後の要素のインデックスを返すラムダ式を定義します。  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [How to: Create a Lambda Expression](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-lambda-expression.md)   
 [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)