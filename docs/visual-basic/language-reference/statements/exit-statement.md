---
title: "Exit Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Exit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "execution, ending"
  - "files, closing"
  - "programs, quitting"
  - "code, exiting"
  - "Exit statement"
  - "program termination"
  - "execution, stopping"
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exit Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロシージャまたはブロックを終了し、そのプロシージャ呼び出しまたはブロック定義の次のステートメントに即座に制御を移します。  
  
## 構文  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## ステートメント  
 `Exit Do`  
 このステートメントのある `Do` ループを直ちに抜けます。  `Loop` ステートメントの後ろのステートメントから実行が継続されます。  `Exit Do` が使用できるのは `Do` ループの中だけです。  入れ子構造になっている `Do` ループの中で使用すると、`Exit Do` は内側のループを抜け、入れ子構造の 1 つ外側のレベルに制御を移します。  
  
 `Exit For`  
 このステートメントのある `For` ループを直ちに抜けます。  `Next` ステートメントの後ろのステートメントから実行が継続されます。  `Exit For` が使用できるのは `For`...`Next` ループまたは `For Each`...`Next` ループの中だけです。  入れ子構造になっている `For` ループの中で使用すると、`Exit For` は内側のループを抜け、入れ子構造の 1 つ外側のレベルに制御を移します。  
  
 `Exit Function`  
 このステートメントのある `Function` プロシージャを直ちに抜けます。  `Function` プロシージャを呼び出したステートメントの後ろのステートメントから実行が継続されます。  `Exit Function` が使用できるのは `Function` プロシージャの中だけです。  
  
 戻り値を指定するには、`Exit Function` ステートメントより前の行で関数名に値を割り当てます。  1 つのステートメントで戻り値を割り当てて関数を抜けるには、[Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) を使用します。  
  
 `Exit Property`  
 このステートメントのある `Property` プロシージャを直ちに抜けます。  `Property` プロシージャを呼び出したステートメント、つまりプロパティの値を要求または設定しているステートメントから実行が継続されます。  `Exit Property` が使用できるのは、プロパティの `Get` プロシージャまたは `Set` プロシージャの中だけです。  
  
 `Get` プロシージャで戻り値を指定するには、`Exit Property` ステートメントより前の行で関数名に値を割り当てます。  1 つのステートメントで戻り値を割り当てて `Get` プロシージャを抜けるには、`Return` ステートメントを使用します。  
  
 `Set` プロシージャでは、`Exit Property` ステートメントと `Return` ステートメントは同等です。  
  
 `Exit Select`  
 このステートメントのある `Select Case` を直ちに抜けます。  `End Select` ステートメントの後ろのステートメントから実行が継続されます。  `Exit Select` が使用できるのは `Select Case` ステートメントの中だけです。  
  
 `Exit Sub`  
 このステートメントのある `Sub` プロシージャを直ちに抜けます。  `Sub` プロシージャを呼び出したステートメントの後ろのステートメントから実行が継続されます。  `Exit Sub` が使用できるのは `Sub` プロシージャの中だけです。  
  
 `Sub` プロシージャでは、`Exit Sub` ステートメントと `Return` ステートメントは同等です。  
  
 `Exit Try`  
 このステートメントのある `Try` ブロックまたは `Catch` ブロックを直ちに抜けます。  `Finally` ブロックが 1 つ存在する場合はそこから、そうでない場合は `End Try` ステートメントの後ろのステートメントから実行を継続します。  `Exit Try` が使用できるのは `Try` ブロックまたは `Catch` ブロックの中だけです。`Finally` ブロックの中では使用できません。  
  
 `Exit While`  
 このステートメントのある `While` ループを直ちに抜けます。  `End While` ステートメントの後ろのステートメントから実行が継続されます。  `Exit While` が使用できるのは `While` ループの中だけです。  `While` ループが入れ子構造になっている場合、`Exit While` のあるループの 1 つ外側のループに制御が移ります。  
  
## 解説  
 この `Exit` ステートメントと `End` ステートメントを混同しないでください。  `Exit` はステートメントの終了を定義するステートメントではありません。  
  
## 使用例  
 次の例では、`index` 変数が 100 を上回ったときに、ループ条件によってループが停止されます。  ただし、ループ内の `If` ステートメントにより、index 変数が 10 を上回ったときに、`Exit Do` ステートメントによってループが停止されます。  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## 使用例  
 戻り値を `myFunction` という名前の関数に割り当てて、`Exit Function` を使って関数から戻すコード例を次に示します。  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## 使用例  
 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) を使用して戻り値を割り当てて、関数を抜けるコード例を次に示します。  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## 参照  
 [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)   
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)   
 [Stop Statement](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)