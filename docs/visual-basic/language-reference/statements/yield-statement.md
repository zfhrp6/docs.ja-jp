---
title: "Yield ステートメント (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Yield"
helpviewer_keywords: 
  - "反復子, Yield ステートメント [Visual Basic:"
  - "反復子 [Visual Basic]"
  - "Yield ステートメント [Visual Basic]"
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Yield ステートメント (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`For Each...Next` のステートメントにコレクションの次の要素を送信します。  
  
## 構文  
  
```  
Yield expression  
```  
  
#### パラメーター  
  
|||  
|-|-|  
|語句|定義|  
|`expression`|必須です。  `Yield` のステートメントを含む `Get` の反復子関数またはアクセサーの型に暗黙に変換できる式。|  
  
## 解説  
 `Yield` のステートメントは、コレクションの 1 種類の要素を一度に返します。  `Yield` のステートメントは、コレクションに対するカスタムの反復を実行 `Get` のアクセサー含まれており、または反復子関数で。  
  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md) または LINQ クエリを使用して、反復子の関数を実行します。  `For Each` ループの各反復で反復子の関数を呼び出します。  `Yield` のステートメントが反復子関数に到達すると、`expression` は戻り、コードの現在の位置は保持されます。  実装はその位置から反復子関数が呼び出されると、に再起動されます。  
  
 暗黙の変換は `Yield` のステートメントの `expression` の型から反復子の戻り値の型にする必要があります。  
  
 イテレーションの末尾に `Exit Function` または `Return` のステートメントを使用できます。  
  
 " `Get` の `Iterator` の関数またはアクセサーで使用されている場合にのみ" yield に予約語ではなく、特別な意味を持ちます。  
  
 反復子の関数と `Get` のアクセサーの詳細については、[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)を参照してください。  
  
## 反復子の関数は、アクセサーを取得し、  
 `Get` の反復子関数またはアクセサーの申告は、次の条件を満たす必要があります:  
  
-   これは [&#91;反復子&#93;](../../../visual-basic/language-reference/modifiers/iterator.md) 修飾子を含める必要があります。  
  
-   戻り値の型は <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601>である必要があります。  
  
-   これは `ByRef` のパラメーターを持つことはできません。  
  
 反復子の関数は、イベント インスタンス コンストラクター、静的コンストラクター、またはデストラクターで静的含めることはできません。  
  
 反復子の関数は、匿名関数です。  詳細については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 例外処理  
 `Yield` のステートメントは [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)の `Try` ブロックの中にある場合もあります。  `Yield` のステートメントがある `Try` ブロックは `Catch` ブロックを持ち `Finally` のブロックを指定できます。  
  
 `Yield` のステートメントは `Catch``Finally` ブロックまたはブロック内に置くことはできません。  
  
 反復子関数 \(外\) `For Each` の本体で例外をスローする場合、反復子関数の `Catch` ブロックは実行されませんが、反復子関数の `Finally` ブロックが実行されます。  反復子関数のブロック `Catch` は、反復子関数内で発生した例外のみをキャッチします。  
  
## 技術的な実装  
 次のコードは、反復子関数から `IEnumerable (Of String)` を返し、をに `IEnumerable (Of String)`の要素に繰り返します。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 `MyIteratorFunction` の呼び出しは関数の本体は実行されません。  代わり `elements` の呼び出しは、変数に `IEnumerable(Of String)` を返します。  
  
 `For Each` のループ反復で、<xref:System.Collections.IEnumerator.MoveNext%2A> のメソッドは `elements`に対して呼び出されます。  この呼び出しは `Yield` の次のステートメントに到達するまで `MyIteratorFunction` の本体を実行します。  `Yield` のステートメントはループ本体で使用するための `element` 変数の値 `IEnumerable (Of String)`である、またはの要素のプロパティを <xref:System.Collections.Generic.IEnumerator%601.Current%2A> だけでなく、決定しますが、式を返します。  
  
 `For Each` ループの各反復で、反復子本体の実行は `Yield` ステートメントに到達するときに中断した場所からか続行され、もう一度停止します。  `For Each` ループの反復子は関数または `Return` または `Exit Function` ステートメントの最後に到達すると完了します。  
  
## 使用例  
 次の例に [次に、…](../../../visual-basic/language-reference/statements/for-next-statement.md) のループ内にある `Yield` のステートメントがあります。  `Main` の [&#91;For Each&#93;](../../../visual-basic/language-reference/statements/for-each-next-statement.md) のステートメント本体の各反復で `Power` の反復子の関数への呼び出しを作成します。  反復子の関数に対する各呼び出しは `For…Next` のループの次の反復処理中に発生する `Yield` の次のステートメントの実行に移動します。  
  
 反復子メソッドの戻り値の型は <xref:System.Collections.Generic.IEnumerable%601>の反復子のインターフェイス型です。  反復子のメソッドが呼び出されると、数値の累乗を含む列挙可能なオブジェクトを返します。  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## 使用例  
 次の例は、反復子である `Get` のアクセサーを示します。  プロパティの申告は `Iterator` 修飾子が含まれます。  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 その他の例については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 必要条件  
 [!INCLUDE[vs_dev11_long](../../../csharp/includes/vs_dev11_long_md.md)]  
  
## 参照  
 [反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)   
 [Statements](../../../visual-basic/language-reference/statements/index.md)