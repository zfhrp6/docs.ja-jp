---
title: "Function プロシージャ (Visual Basic) | Microsoft Docs"
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
  - "Function プロシージャ"
  - "戻り値、Function プロシージャ"
  - "Visual Basic コード、プロシージャ"
  - "プロシージャ、呼び出し"
  - "プロシージャ、Function プロシージャ"
  - "構文、Function プロシージャ"
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Function プロシージャ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Function` プロシージャは、`Function` ステートメントと `End Function` ステートメントで囲まれた一連の [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ステートメントです。  `Function` プロシージャはタスクを実行した後、呼び出し元のコードに制御を戻します。  制御を戻すとき、値も呼び出し元のコードに返します。  
  
 プロシージャが呼び出されるたびに、`Function` ステートメント後の最初の実行可能なステートメントから、最初の `End Function`、`Exit Function`、または `Return` ステートメントまでの一連のステートメントが実行されます。  
  
 `Function` プロシージャはモジュール、クラス、または構造体に定義できます。  既定で `Public` に設定されます。つまり、プロシージャを定義したモジュール、クラス、または構造体へのアクセスが可能なアプリケーション内のどこからでも呼び出すことができます。  
  
 また、`Function` プロシージャは、呼び出し元のコードによって渡される定数、変数、式などの引数を受け取ることができます。  
  
## 宣言の構文  
 `Function` プロシージャを宣言する構文は次のとおりです。  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *modifiers* には、アクセス レベルのほか、オーバーロード、オーバーライド、共有、およびシャドウに関する情報を指定できます。  詳細については、「[Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)」を参照してください。  
  
 各パラメーターは、[Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) の場合と同じ方法で宣言します。  
  
### \[データ型\]  
 すべての `Function` プロシージャには、変数と同じようにデータ型があります。  このデータ型は `Function` ステートメント内の `As` 句で指定し、関数が呼び出し元のコードに返す値のデータ型を決定します。  たとえば、次のようになります。  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 詳細については、「[Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)」の "指定項目" を参照してください。  
  
## 戻り値  
 `Function` のプロシージャから呼び出し元のコードに返される値は、戻り値と呼ばれます。  プロシージャが値を返すには、次の 2 とおりの方法があります。  
  
-   `Return` ステートメントを使用して戻り値を指定します。この場合は、呼び出し元のプログラムに制御がすぐに戻されます。  次に例を示します。  
  
    ```vb  
    Function FunctionName [(ParameterList)] As ReturnType  
        ' The following statement immediately transfers control back  
        ' to the calling code and returns the value of Expression.  
        Return Expression  
    End Function  
    ```  
  
-   プロシージャのステートメントの自身の関数名に値を代入します。  `Exit Function` ステートメントまたは `End Function` ステートメントが実行されるまで、呼び出し元のプログラムに制御が戻されません。  次に例を示します。  
  
    ```vb  
    Function FunctionName [(ParameterList)] As ReturnType  
        ‘ The following statement does not transfer control back to the calling code.  
        FunctionName = Expression  
        ' When control returns to the calling code, Expression is the return value.  
    End Function  
    ```  
  
 戻り値を関数名に代入する方法の利点は、`Exit Function` ステートメントまたは `End Function` ステートメントが実行されるまで、プロシージャから制御が戻されないという点にあります。  これにより、一時的な値を代入して、後で必要に応じて調整できます。  
  
 返される値の詳細については、[Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)を参照してください。  返される配列については、[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)を参照してください。  
  
## 呼び出し構文  
 `Function` プロシージャを呼び出すには、代入ステートメントの右側または式の中に、名前と引数を指定します。  省略できないすべての引数の値を指定し、引数リストをかっこで囲む必要があります。  指定する引数がない場合は、かっこを省略することもできます。  
  
 `Function` プロシージャを呼び出す構文は次のとおりです。  
  
 *左辺値* `=` *functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *functionname* `[(` *argumentlist* `)] / 3) <=` *式* `) Then`  
  
 `Function` プロシージャを呼び出すときには、必ずしも戻り値を使用する必要はありません。  戻り値を使用しない場合も、戻り値が無視されるだけで、プロシージャのアクションはすべて実行されます。  <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> はたびたびこの方法で呼び出されます。  
  
### 宣言と呼び出しの説明  
 次の `Function` プロシージャは、直角三角形の最も長い辺 \(斜辺\) を他の 2 つの辺の値を基に計算します。  
  
 [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/function-procedures_1.vb)]  
  
 `hypotenuse` を呼び出す一般的な例を次に示します。  
  
 [!code-vb[VbVbcnProcedures#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/function-procedures_2.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)