---
title: "For...Next ステートメント (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Step"
  - "vb.Next"
  - "vb.To"
  - "vb.for"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "無限ループ"
  - "Next キーワード, For...Next ステートメント"
  - "For キーワード [Visual Basic], For...Next ステートメント"
  - "Step キーワード, For...Next ステートメント"
  - "演算子のオーバーロード, For...Next ステートメント"
  - "To キーワード, For...Next ステートメント"
  - "無限ループ"
  - "ループ, 無限"
  - "命令, 繰り返し"
  - "Next ステートメント, For...Next"
  - "For...Next ステートメント"
  - "ループ構造, For...Next"
  - "ループ, 無限"
  - "Exit ステートメント, For...Next ステートメント"
  - "For ステートメント"
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
caps.latest.revision: 64
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 64
---
# For...Next ステートメント (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定された回数だけ、一連のステートメントを繰り返すフロー制御ステートメントです。  
  
## 構文  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## 指定項目  
  
|指定項目|説明|  
|----------|--------|  
|`counter`|`For` ステートメントには必ず指定します。  数値変数を指定します。  このループの制御変数になります。  詳細については、このトピックで後述する「[counter 引数](#BKMK_Counter)」を参照してください。|  
|`datatype`|省略可能です。  `counter` のデータ型を指定します。  詳細については、このトピックで後述する「[counter 引数](#BKMK_Counter)」を参照してください。|  
|`start`|必須です。  数式を指定します。  `counter` の初期値になります。|  
|`end`|必須です。  数式を指定します。  `counter` の最終値になります。|  
|`step`|省略可能です。  数式を指定します。  ループを 1 回実行するごとに引数 `counter` を増やす量です。|  
|`statements`|省略可能です。  `For` と `Next` の間に記述したステートメントは、指定した回数だけ実行されます。|  
|`Continue For`|省略可能です。  制御をループの次の反復処理に移します。|  
|`Exit For`|省略可能です。  制御を `For` ループの外に移します。|  
|`Next`|必須です。  `For` ループの定義を終了します。|  
  
> [!NOTE]
>  このステートメントで `To` のキーワードがカウンターの範囲を指定するために使用されます。  また [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) と配列申告でこのキーワードを使用できます。  配列の宣言の詳細については、「[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)」を参照してください。  
  
## 簡単な例  
 回数の一連のステートメントを繰り返し実行する場合に `For`…`Next` の構造を使用します。  
  
 次の例では、1 の値を持つ `index` の変数の先頭は `index` の到達 5.の値の後に終了した場合は、ループ反復ごとにインクリメントします。  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_1.vb)]  
  
 次の例では、2 時の `number` の変数の先頭は `number` の到達 0 の値の終了後にループの各反復処理の軽減され、0.25。  `-.25` の `Step` の引数はループの各反復で値 0.25 が低くなります。  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  ループまたはのステートメントを実行する回数先立ってわからない場合 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) か [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) は適しています。  一方、指定の回数だけループを実行する場合は、`For`...`Next` ループが最適です。  このループでは、最初にループに入るときに、繰り返しの回数を決定します。  
  
## ループの入れ子  
 `For` ループは入れ子構造にできます。つまり、ループの中に別のループを入れることができます。  次の例は、それぞれ異なる step 値を指定した入れ子になった `For`...`Next` 構造体を示しています。  外側のループでは、ループの反復処理が実行されるたびに文字列が作成されます。  内側のループでは、ループの反復処理が実行されるたびにループ カウンター変数がデクリメントされます。  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_3.vb)]  
  
 ループの入れ子は、各ループに一意の変数を `counter` ある必要があります。  
  
 また、さまざまな種類の制御構造を入れ子にすることもできます。  詳細については、「[Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。  
  
## の終了、のを続行します。  
 `Exit For` のステートメントは `Next` のステートメントの次のステートメントにすぐに `For`\[…\]`Next` のループおよび制御を移し終了します。  
  
 `Continue For` ステートメントは、制御をループの次の反復処理に直ちに移します。  詳細については、「[Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)」を参照してください。  
  
 次の例は、`Continue For` ステートメントと `Exit For` ステートメントの使用方法を示しています。  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_4.vb)]  
  
 `Exit For` ステートメントは、`For`…`Next` ループで何度でも使用できます。  入れ子構造になっている `For`…`Next` ループ内で使用すると、`Exit For` は最も内側のループを抜け、入れ子構造の 1 つ外側のレベルに制御を移します。  
  
 `Exit For` は条件を評価した後によく使用されます \(たとえば、`If`…`Then`…`Else` の構造体\)  次のような条件の場合に `Exit For` を使用できます。  
  
-   ループの継続が不要または不可能である。  エラー値または終了要求はこの要件を作成する場合があります。  
  
-   `Try`…`Catch`…`Finally` のステートメントで例外をキャッチします。  `Finally` ブロックの最後で `Exit For` を使用できます。  
  
-   大きい、または無限実行回数が多いループになります。無限ループがあります。  このような条件を検出した場合は、`Exit For` を使用してループを抜けることができます。  詳細については、「[Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)」を参照してください。  
  
## 技術的な実装  
 `For`...`Next` ループが開始されると、`start`、`end`、および `step` が評価されます。  Visual Basic は、現時点でのみこれらの値を評価し、`counter`に `start` を再配置。  ステートメント ブロックの実行、Visual Basic が `end`に `counter` を比較する前に、  `counter` が既に場合は `step` が負の場合 `end` の値 \(またはそれより小さい\)、`Next` のステートメントの次のステートメントに `For` のループの終わりとコントロールのパス。  それ以外の場合は、ステートメント ブロックが実行されます。  
  
 `Next` ステートメントが実行されるたびに、`step` の値が `counter` に加算され、`For` ステートメントに戻ります。  その後、`counter` と `end` が再び比較され、その結果に応じて、ステートメント ブロックが再度実行されるかループが終了します。  このプロセスは、`counter` が `end` を超えるか、`Exit For` ステートメントに到達するまで継続されます。  
  
 ループは `counter` が `end`を通過するまで停止しません。  `counter` と `end` が等しい場合にはループは継続されます。  ブロックの実行を行うかどうかは、`step` が正の場合は `counter` \<\= `end` の比較によって決定され、`step` が負の場合は `counter` \>\= `end` の比較によって決定されます。  
  
 ループ内での値を `counter` ときに、変更する、コードが読みにくく、デバッグが困難な場合があります。  `start`の値を変更して、`end`、または `step` は、最初のループに入る時点で決定されるとイテレーションの値には影響しません。  
  
 ループになっている場合、コンパイラは内部のレベルの `Next` のステートメントの前に外側の入れ子レベルの `Next` のステートメントが発生した場合はエラーを発行します。  ただし、コンパイラがこのエラーを検出できるのは、すべての `Next` ステートメントに `counter` を指定した場合に限られます。  
  
### step 引数  
 `step` には正の数または負の数を指定できます。  このパラメーターには、次の表に従って、ループの処理方法を決定します:  
  
|**ステップの値**|**実行条件**|  
|----------------|--------------|  
|正の数または 0|`counter` \<\= `end`|  
|負|`counter` \>\= `end`|  
  
 `step` の既定値は 1 です。  
  
###  <a name="BKMK_Counter"></a> counter 引数  
 次の表は `counter` が `For…Next` のループ スコープに新しいローカル変数を定義するかどうかを示します。  この確認は `datatype` があるかどうか、および `counter` が既に定義されているかどうかによって異なります。  
  
|`datatype` ですか。|`counter` は既に定義されていますか。|\(`counter` が `For...Next` のループ スコープに新しいローカル変数を定義するかどうか結果\)|  
|---------------------|-----------------------------|-----------------------------------------------------------------|  
|Ｘ|○|`counter` が既に定義されているため、No。  `counter` の範囲がプロシージャにローカルである、コンパイル時に警告が発生します。|  
|Ｘ|Ｘ|はい。  データ型は `start`、`end`と `step` の式から推論されます。  型の推論については、[Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) と [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)を参照してください。|  
|○|○|`counter` の既存の変数がプロシージャの外部で定義された場合にのみ○ \(ただし。  この変数は別に残ります。  `counter` の既存の変数のスコープがプロシージャにローカルな場合、コンパイル エラーが発生します。|  
|○|Ｘ|はい。|  
  
 `counter` のデータ型は次の型の 1 つが必要があるイテレーションの型が決まります:  
  
-   `Byte`、`SByte`、`UShort`、`Short`、`UInteger`、`Integer`、`ULong`、`Long`、`Decimal`、`Single`、または `Double`。  
  
-   [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) を使用して宣言した列挙型。  
  
-   `Object`。  
  
-   次の演算子を含む `T` 型。`B` は `Boolean` 式で使用できる型です。  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 `Next` のステートメントに `counter` 変数を指定できます。  この構文は、特に `For` の入れ子になったループ、プログラムの読みやすさが向上します。  `For` のステートメントに表示される変数を指定する必要があります。  
  
 `start`、`end`、および `step` には、`counter` と同じ型に拡張可能な任意のデータ型として評価される式を指定できます。  `counter`のユーザー定義型を使用すると、`counter`の種類に `start`、`end`、または `step` の型を変換するには `CType` の変換演算子を定義しなければならない場合があります。  
  
## 使用例  
 次の例では、ジェネリック リストからすべての要素を削除しています。  [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)の代わりに、降順で繰り返し発生 `For`…`Next` のステートメントを示しています。  この例では `removeAt` のメソッドに、削除された要素の後に要素のインデックス値が小さくなるため、この方法を使用します。  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_5.vb)]  
  
## 使用例  
 次の例では、[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)を使用して宣言された列挙型を繰り返します。  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_6.vb)]  
  
## 使用例  
 次の例では、ステートメントのパラメーターで `+`、`-`、`>=`、および `<=` の各演算子のオーバーロードを持つクラスを使用しています。  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_7.vb)]  
  
## 参照  
 <xref:System.Collections.Generic.List%601>   
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)