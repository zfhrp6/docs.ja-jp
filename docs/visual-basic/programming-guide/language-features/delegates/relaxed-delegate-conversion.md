---
title: "Relaxed Delegate Conversion (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "relaxed delegate conversion [Visual Basic]"
  - "delegates [Visual Basic], relaxed conversion"
  - "conversions, relaxed delegate"
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Relaxed Delegate Conversion (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

厳密でないデリゲート変換という機能を使用することで、シグネチャが同じでない場合も Sub や関数をデリゲートやハンドラーに割り当てることができます。したがって、メソッド呼び出しの中で既に認められているバインディングに合わせて、デリゲートへのバインディングを統一できるようになります。  
  
## パラメーターと戻り値の型  
 厳密でない変換の場合は、`Option Strict` が `On` に設定されていても、シグネチャの厳密な一致ではなく以下の条件が必要になります。  
  
-   デリゲートの各パラメーターのデータ型から、対応する関数または `Sub` の対応するパラメーターのデータ型への変換が、拡大変換になっている必要があります。  以下の例では、`Del1` デリゲートに `Integer` という 1 つのパラメーターがあります。  対応するラムダ式のパラメーター `m` のデータ型は、`Integer` からの拡大変換に相当するデータ型 \(`Long` や `Double` など\) でなければなりません。  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     縮小変換は、`Option Strict` が `Off` に設定されている場合のみ許可されます。  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   対応する関数または `Sub` の戻り値の型からデリゲートの戻り値の型への変換も、拡大変換になっている必要があります。  `del1` の戻り値の型が `Integer` であるため、以下の例では、対応する各ラムダ式の本体が、`Integer` からの拡大変換に相当するデータ型に評価される必要があります。  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 `Option Strict` が `Off` に設定されている場合は、拡大変換は両方向で削除されます。  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## パラメーター指定の省略  
 厳密でないデリゲートの場合は、対応するメソッドの中でパラメーターの指定を完全に省略することも可能です。  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 一部のパラメーターを指定して、その他のパラメーターを省略することはできません。  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 パラメーターを省略する書き方は、複雑なパラメーターがいくつもかかわっているイベント ハンドラーを定義する場合などに便利です。  イベント ハンドラーは、場合によっては引数を使用しないことがあります。  つまり、イベントが登録されているコントロールの状態に直接アクセスして、引数を無視する、という場合です。  厳密でないデリゲートでは、あいまいさを残さない限り、そのような宣言で引数を省略してもかまいません。  たとえば、パラメーターを完全に指定した以下の `OnClick` メソッドは、`RelaxedOnClick` として書き換えることができます。  
  
```vb#  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## AddressOf の例  
 前の例では、ラムダ式を使用して、型の関係を見やすくしていました。  ところが、`AddressOf`、`Handles`、`AddHandler` のいずれかを使用するデリゲートの割り当てでも、同じような厳密でない書き方が可能です。  
  
 以下の例では、関数 `f1`、`f2`、`f3`、`f4` をすべて `Del1` に割り当てることができます。  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 次の例は、`Option Strict` が `Off` に設定されている場合のみ有効です。  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## 関数の戻り値の排除  
 厳密でないデリゲート変換では、関数を `Sub` デリゲートに割り当てることによって、関数の戻り値を事実上無視することも可能です。  一方、`Sub` を関数デリゲートに割り当てることはできません。  以下の例では、関数 `doubler` のアドレスを `Sub` デリゲート `Del3` に割り当てています。  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## 参照  
 [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)