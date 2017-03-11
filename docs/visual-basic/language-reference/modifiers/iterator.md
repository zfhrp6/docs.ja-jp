---
title: "Iterator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Iterator"
helpviewer_keywords: 
  - "Iterator keyword [Visual Basic]"
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Iterator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Get` 関数またはアクセサーが反復子であることを指定します。  
  
## 解説  
 *反復子は* コレクション上のカスタム反復処理します。  反復子はコレクションの各要素を一つずつ返すために [Yield,yield](../../../visual-basic/language-reference/statements/yield-statement.md) ステートメントを使用します。  `Yield` ステートメントに到達すると、コードの現在の位置は保持されます。  実装はその場所から反復子関数の呼び出しを再起動します。  
  
 反復子は、関数またはプロパティ定義の `Get` のアクセサーとして実行できます。  `Iterator` の修飾子は `Get` の反復子関数またはアクセサーの宣言に表示されます。  
  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)を使用してクライアント コードからの反復子をダイヤルします。  
  
 `Get` の反復子関数またはアクセサーの戻り値の型は <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601>を使用できます。  
  
 反復子は `ByRef` パラメーターを持つことができません。  
  
 反復子は、イベント インスタンス コンストラクター、静的コンストラクター、または静的デストラクターには発生しません。  
  
 反復子は、匿名関数です。  詳細については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 反復子の詳細については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 使用方法  
 修飾子 `Iterator` は、次の構文で使用します。  
  
-   [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## 使用例  
 次の例は、反復子の関数を示します。  反復子の関数に [For… Next には](../../../visual-basic/language-reference/statements/for-next-statement.md) のループ内にある `Yield` ステートメントがあります。  `Main` の [各には](../../../visual-basic/language-reference/statements/for-each-next-statement.md) のステートメント本体の各反復で `Power` の反復子関数に呼び出しを作成します。  反復子の関数に対する各呼び出しは `For…Next` のループの次の反復処理中に発生する `Yield` ステートメントの次の実行に進みます。  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/iterator_1.vb)]  
  
## 使用例  
 次の例は、反復子である `Get` のアクセサーを示します。  `Iterator` の修飾子は、プロパティ宣言にあります。  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/iterator_2.vb)]  
  
 その他の例については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 参照  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>   
 [反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)   
 [Yield ステートメント](../../../visual-basic/language-reference/statements/yield-statement.md)