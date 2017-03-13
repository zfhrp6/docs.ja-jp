---
title: "GoTo Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.GoTo"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GoTo statement"
  - "control flow, branching"
  - "unconditional branching"
  - "branching"
  - "branching, unconditional"
  - "branching, conditional"
  - "conditional statements, GoTo statement"
  - "GoTo statement, syntax"
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# GoTo Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャ内の指定した行に無条件に分岐します。  
  
## 構文  
  
```  
GoTo line  
```  
  
## 指定項目  
 `line`  
 必ず指定します。  任意の行ラベルを指定します。  
  
## 解説  
 `GoTo` ステートメントの分岐先は、同じプロシージャ内だけです。他のプロシージャには分岐できません。  分岐先の行には、`GoTo` が参照するための行ラベルが必要です。  詳細については、「[How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)」を参照してください。  
  
> [!NOTE]
>  `GoTo` ステートメントを使用すると、プログラムが読みにくくなり、保守が困難になります。  可能な限り、制御構造を使うようにしてください。  詳細については、「[Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md)」を参照してください。  
  
 `GoTo` ステートメントを、`For`...`Next`、`For Each`...`Next`、`SyncLock`...`End SyncLock`、`Try`...`Catch`...`Finally`、`With`...`End With`、または `Using`...`End Using` の外部から内部のラベルへの分岐に使うことはできません。  
  
## 分岐と Try 構築  
 `Try`...`Catch`...`Finally` 構築の内部では、`GoTo` ステートメントによる分岐に以下の規則が適用されます。  
  
|ブロックまたは領域|外部から内部への分岐|内部から外部への分岐|  
|---------------|----------------|----------------|  
|`Try` ブロック|同じ構築の `Catch` ブロックからのみ分岐可能 <sup>1</sup>|構築全体の外部へのみ分岐可能|  
|`Catch` ブロック|不可|構築全体の外部、または同じ構築の `Try` ブロックへの分岐のみ可能 <sup>1</sup>|  
|`Finally` ブロック|不可|不可|  
  
 <sup>1</sup> ある `Try`...`Catch`...`Finally` 構築が別の構築の中に入れ子になっている場合、`Catch` ブロックから自分と同じレベルの `Try` ブロックへの分岐は可能ですが、それ以外の `Try` ブロックへは分岐できません。  入れ子にされた `Try`...`Catch`...`Finally` 構築は、外側の構築の `Try` ブロックまたは `Catch` ブロック内に完全に含まれていることが必要です。  
  
 次の例では、`Try` 構築が別の構築にネストされています。  2 つの構築のブロックどうしのさまざまな分岐について、有効または無効を示してあります。  
  
 ![Try 構造内の分岐のグラフィック ダイアグラム](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Try 構築内の有効な分岐と無効な分岐  
  
## 使用例  
 `GoTo` ステートメントを使って、プロシージャ内の行ラベルに分岐するコード例は、次のとおりです。  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## 参照  
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)