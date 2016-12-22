---
title: "While...End While Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.While"
  - "vb.While...EndWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "While statement, While...End While"
  - "While statement"
  - "While...End While statements"
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# While...End While Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定された条件が真 \(`True`\) である間、一連のステートメントを繰り返し実行します。  
  
## 構文  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`condition`|必須。  `Boolean` 式を指定します。  `condition` が `Nothing` の場合、Visual Basic はこれを `False` として扱います。|  
|`statements`|省略可能。   1 つ以上のステートメントを `While` の後に指定します。この部分は、`condition` が `True` であるたびに実行されます。|  
|`Continue While`|省略可能。  `While` ブロックの次の反復処理に制御を移します。|  
|`Exit While`|省略可能。  制御を `While` ブロックの外へ移動します。|  
|`End While`|必須。  `While` ブロックの定義を終了します。|  
  
## 解説  
 条件が `True` の間、一連のステートメントを不特定の回数繰り返すには、`While...End While` 構造を使用します。  条件をテストする場所またはテスト結果の判定を柔軟に指定する必要がある場合は、[Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) の方が適しています。  ステートメントを特定の回数繰り返す場合は、[For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md) を使用することをお勧めします。  
  
> [!NOTE]
>  `While` キーワードは、[Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)、[Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)、および [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md) でも使用されます。  
  
 `condition` が `True` である場合、`End While` が現れるまですべての `statements` が実行されます。  コントロールは `While` のステートメントに戻されて、`condition` は再チェックされます。  `condition` が真 \(`True`\) の間、この処理が繰り返されます。  これは `False`場合、コントロールは `End While` のステートメントの次のステートメントに渡されます。  
  
 `While` のステートメントは、ループを開始する前に必ず条件を確認します。  条件が `True` である限りループが継続されます。  ループに最初に入ったとき `condition` が `False` 場合、一度も実行されません。  
  
 `condition` は、通常 2 の値の比較に生成されますが、[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) には、の値を評価する式です \(`True` か `False`\)。  この式は異なるデータ型の値が、`Boolean`に変換された数値型なども指定できます。  
  
 `While` ループは入れ子構造にできます。つまり、ループの中に別のループを入れることができます。  また、種類の異なる制御構造を入れ子にすることもできます。  詳細については、「[Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。  
  
## が、終了します  
 [が、終了します](../../../visual-basic/language-reference/statements/exit-statement.md) のステートメントは `While` のループを終了する別の方法を用意できます。  `End While` のステートメントの次のステートメントにすぐに`Exit While` の制御を移します。  
  
 条件を評価した後、通常 `Exit While` を使用します \(たとえば、`If...Then...Else` の構造体\)   ループの継続が不要になったり不可能になったりする条件 \(エラー値や終了要求など\) を検出した場合にループを終了できます。  大きい場合、または無限実行回数が多いループになります。*無限ループを*引き起こす可能性がある条件をテストする場合 `Exit While` を使用できます。  次に、ループを終了するに `Exit While` を使用できます。  
  
 `Exit While` ステートメントは、`While` ループの任意の場所に何度でも使用できます。  
  
 最も内側のループから入れ子構造の一つ外側のレベルに `While` の `Exit While`、入れ子になったループの制御を移します内で使用された場合。  
  
 ループの次の反復処理に直ちに `Continue While` のステートメントの制御を移します。  詳細については、「[Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)」を参照してください。  
  
## 使用例  
 次の例では、`index` 変数が 10 を上回るまで、ループ内のステートメントが実行され続けます。  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## 使用例  
 次の例は、`Continue While` ステートメントと `Exit While` ステートメントの使用方法を示しています。  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## 使用例  
 次の例では、テキスト ファイルのすべての行が読み取られます。  <xref:System.IO.File.OpenText%2A> メソッドによりファイルが開かれ、文字を読み取る <xref:System.IO.StreamReader> が返されます。  `While` では、`StreamReader` の <xref:System.IO.StreamReader.Peek%2A> のメソッドは、ファイルが追加の文字が含まれているかどうかを判定します。  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## 参照  
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)