---
title: "Continue Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.continue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Continue statement [Visual Basic]"
  - "loops, transferring to next iteration"
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Continue Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

制御をループの次の反復処理に直ちに移します。  
  
## 構文  
  
```  
Continue { Do | For | While }  
```  
  
## 解説  
 `Do`、`For`、または `While` ループの内側から、そのループの次の反復処理に制御を移すことができます。  制御は直ちにループ条件のテストに移動します。つまり、`For` ステートメントか `While` ステートメント、または `Until` 句か `While` 句を含む `Do` ステートメントか `Loop` ステートメントに移動します。  
  
 `Continue` は制御の移動を許可するループの任意の場所に定義できます。  制御の移動を許可する規則は、[GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md)の場合と同じです。  
  
 たとえば、ループ全体が `Try` ブロック、`Catch` ブロック、または `Finally` ブロックの内部にある場合は、`Continue` を使用してループの外部に制御を移動できます。  一方、ループ内に `Try`...`End Try` 構造がある場合は、`Continue` を使用して制御を `Finally` ブロックの外部に移動できず、`Try`...`End Try` 構造の外部に制御を完全に移動する場合に限り、`Try` ブロックまたは `Catch` ブロックの外部に移動できます。  
  
 `Do` ループの内部に別の `Do` ループがあるなど、同じ種類のループが入れ子になっている場合、`Continue Do` ステートメントは自分が定義されている内側の `Do` ループの次の反復処理にスキップします。  `Continue` を使用して、同じ種類の外側のループの次の反復処理にスキップすることはできません。  
  
 `For` ループの内部に `Do` ループがあるなど、種類の異なるループが入れ子になっている場合、`Continue Do` または `Continue For` を使用することによって、どちらのループの次の反復処理にもスキップできます。  
  
## 使用例  
 次のコード例は `Continue While` ステートメントを使用して、除数が 0 の場合に配列の次の列にスキップします。  `Continue While` は `For` ループの内部にあります。  制御は `For` ループを含む内側の `While` ループの次の反復処理である `While col < lastcol` ステートメントに移ります。  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## 参照  
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)