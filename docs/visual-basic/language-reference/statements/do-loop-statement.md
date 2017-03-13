---
title: "Do...Loop Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Do"
  - "vb.Loop"
  - "vb.Until"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conditional statements, Do…Loop"
  - "while statement, Do...Loop"
  - "execution, conditional"
  - "Do loops"
  - "Until keyword, Do...Loop statement"
  - "Do...Loop statement"
  - "instructions, repeating"
  - "Do statement"
  - "Exit statement, in Do...Loop statements"
  - "loop structures, Do…Loop statements"
  - "do-while statements"
  - "loops, exiting"
  - "Loop keyword, Do...Loop statement"
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: 37
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 37
---
# Do...Loop Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定されたブール型 \(`Boolean`\) の条件が真 \(`True`\) である間、または条件が真 \(`True`\) になるまで、一連のステートメントを繰り返します。  
  
## 構文  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`Do`|必須。  `Do` ループの定義を開始します。|  
|`While`|`Until` を使用しない場合は、必ず指定します。  `condition` が偽 \(`False`\) になるまでループを繰り返します。|  
|`Until`|`While` を使用しない場合は、必ず指定します。  `condition` が真 \(`True`\) になるまでループを繰り返します。|  
|`condition`|省略可能。  `Boolean` 式を指定します。  `condition` が `Nothing` の場合、Visual Basic はこれを `False` として扱います。|  
|`statements`|省略可能。  `condition` が真 \(`True`\) である間、または真になるまで繰り返し実行される、任意の行数のステートメントを記述します。|  
|`Continue Do`|省略可能。  `Do` のループの次の反復処理に制御を移します。|  
|`Exit Do`|省略可能。  制御を `Do` ループの外に移します。|  
|`Loop`|必須。  `Do` ループの定義を終了します。|  
  
## 解説  
 `Do...Loop` は一連のステートメントを、条件が満たされるまで何度でも繰り返し実行する場合に使用します。  設定した回数だけステートメントを繰り返す場合は、[For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) を選択した方が通常は便利です。  
  
 `While` と `Until` のいずれかを使用して `condition` を指定しますが、両方は使用できません。  
  
 `condition` はループの最初または終わりに 1 回だけテストできます。  `condition` をループの最初に \(`Do` ステートメント内で\) テストする場合、ループが一度も実行されないことがあります。  ループの終わりに \(`Loop` ステートメント内で\) テストする場合、ループは必ず少なくとも 1 回は実行されます。  
  
 条件は、通常、2 つの値の比較によって判断されますが、[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) 値 \(`True` または `False`\) として評価できる式の場合どのような式でも指定できます。  指定できる値には、数値型などのその他のデータ型を `Boolean` に変換した値も含まれます。  
  
 `Do` ループは入れ子構造にできます。つまり、ループの中に別のループを入れることができます。  また、さまざまな種類の制御構造を入れ子にすることもできます。  詳細については、「[Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。  
  
> [!NOTE]
>  `Do...Loop` 構造を使用すると、`condition` が真 \(`True`\) でなくなったときにループを終了するのか、それとも最初に `True` になったときに終了するのかを判断できるので、[While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) を使用するよりも柔軟性が増します。  また、`condition` をループの最初にテストすることも、ループの終わりにテストすることもできます。  
  
## Exit Do  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) ステートメントを使用すると、別の方法で `Do…Loop` を終了できます。  `Exit Do` は、`Loop` ステートメントの次のステートメントにすぐに制御を移します。  
  
 `Exit Do` は、`If...Then...Else` 構造の中などで、なんらかの条件を評価した後によく使用されます。  ループの継続が不要になったり不可能になったりする条件 \(エラー値や終了要求など\) を検出した場合にループを終了できます。  `Exit Do` は、*無限ループ*を引き起こす可能性がある条件をテストする場合などに使用されます。無限ループは、実行回数が多くなる \(または無限に繰り返される\) ループです。  `Exit Do` を使用してループから抜けることができます。  
  
 `Exit Do` ステートメントは、`Do…Loop` の任意の場所に何度でも使用できます。  
  
 入れ子構造になっている `Do` ループの中で使用すると、`Exit Do` は最も内側のループから入れ子構造の 1 つ外側のレベルに制御を移します。  
  
## 使用例  
 次の例では、`index` 変数が 10 を上回るまで、ループ内のステートメントが実行され続けます。  `Until` 句がループの終わりに配置されています。  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## 使用例  
 次の例では、`Until` 句の代わりに `While` 句が使用されており、ループの終わりではなく最初に `condition` がテストされています。  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## 使用例  
 次の例では、`index` 変数が 100 を上回ったときに、`condition` によってループが停止されます。  ただし、ループ内の `If` ステートメントにより、index 変数が 10 を上回ったときに、`Exit Do` ステートメントによってループが停止されます。  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## 使用例  
 次の例では、テキスト ファイルのすべての行が読み取られます。  <xref:System.IO.File.OpenText%2A> メソッドによりファイルが開かれ、文字を読み取る <xref:System.IO.StreamReader> が返されます。  `Do...Loop` 条件で、`StreamReader` の <xref:System.IO.StreamReader.Peek%2A> メソッドにより、その他の文字があるかどうかが判断されます。  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## 参照  
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)