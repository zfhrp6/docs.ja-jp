---
title: "Nothing (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Nothing"
  - "vb.Nothing"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Nothing keyword"
  - "Nothing keyword, syntax"
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: 31
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 31
---
# Nothing (Visual Basic)
[!INCLUDE[vs2017banner](../../visual-basic/developing-apps/includes/vs2017banner.md)]

任意のデータ型の既定値を表します。  参照型の場合既定値は `null` の参照です。  値型の場合既定値が値型が許容であるかによって異なります。  
  
> [!NOTE]
>  null 非許容値型ではVisual Basic の `Nothing` はC\# の `null` とは異なります。  Visual Basic では`Nothing` にnull 非許容値型の変数を設定した場合その変数は宣言型の既定値に設定されます。  C\# では`null` にnull 非許容値型の変数を割り当てコンパイル時のエラーが発生します。  
  
## 解説  
 `Nothing` はデータ型の既定値を表します。  既定値は変数が値型か参照型かによって異なります。  
  
 *値型の*  変数は値を直接含みます。  値型はすべての数値型`Boolean``Char``Date`すべてのすべての構造体と列挙体が含まれています。   *参照型*  の変数をメモリ内でオブジェクトのインスタンスへの参照を格納します。  参照型はクラス配列デリゲート文字列が含まれます。  詳細については、「[Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
 変数が値型の場合`Nothing` の動作は変数を null 許容のデータ型であるかによって異なります。  null 許容値型を表すには型名に `?` の修飾子を追加します。  null 許容型の変数へ `Nothing` を割り当てる `null` に値を設定します。  使用例を含む詳細については、「[Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)」を参照してください。  
  
 変数が許容ではない値型の場合はそれを `Nothing` を割り当てる宣言型の既定値に設定します。  型に変数のメンバーが含まれている場合は、すべてに既定値が設定されます。  次にスカラー型の場合の例を示します。  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 変数が参照型の場合`Nothing` に変数の型の `null` の参照に変数の設定に割り当てられます。  `null` の参照に設定した変数はオブジェクトに関連付けられません。  次に例を示します。  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 null 許容値型または参照 \(\) 変数が `null` かどうかを確認する場合は`= Nothing` または `<> Nothing` を使用しないでください。  `Is Nothing` または `IsNot Nothing` を使用します。  
  
 Visual Basic で文字列の場合は空の文字列が `Nothing` になります。  したがって`"" = Nothing` は TRUE です。  
  
 `Is` 演算子と `IsNot` 演算子を使用した比較の例を次に示します。  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 `As` 句を使用しないで変数を宣言し、それを `Nothing` に設定した場合、その変数の型は `Object` になります。  次に例を示します: `Dim something = Nothing` コンパイル時のエラーが `Option Strict` が有効で`Option Infer` がオフの場合この場合です。  
  
 キーワード `Nothing` をオブジェクト変数に代入すると、その変数はどのオブジェクト インスタンスも参照しなくなります。  それまで変数がインスタンスを参照していた場合は、変数に `Nothing` を設定しても、インスタンス自体が終了することはありません。  インスタンスが終了したとき、関連付けられていたメモリとシステム リソースが解放されるのは、アクティブな参照が残っていないことをガベージ コレクター \(GC: Garbage Collector\) が検出した後だけです。  
  
 `Nothing` は初期化せずバリアントか存在しないデータベース列を表す <xref:System.DBNull> のオブジェクトとは異なります。  
  
## 参照  
 [Dim Statement](../../visual-basic/language-reference/statements/dim-statement.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Lifetime in Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Is Operator](../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)