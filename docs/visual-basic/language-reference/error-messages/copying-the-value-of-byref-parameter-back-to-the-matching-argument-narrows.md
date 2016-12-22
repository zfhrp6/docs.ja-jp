---
title: "Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32053"
  - "vbc32053"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32053"
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

対応するパラメーター型を拡張する引数を指定してプロシージャが呼び出されましたが、パラメーターから引数への変換が縮小変換です。  
  
 クラスまたは構造体を定義するとき、その型を他の型に変換するための 1 つ以上の変換演算子を定義できます。  また、他の型から元のクラス型または構造体の型に戻すための、逆変換演算子も定義できます。  このようなクラス型または構造体の型をプロシージャ呼び出しに使用すると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はこれらの変換演算子を使用して、引数の型を対応するパラメーターの型に変換します。  
  
 引数を [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) で渡した場合に、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は参照を渡すのではなく、引数の値をプロシージャのローカル変数にコピーする場合があります。  このようなケースでは、プロシージャから制御が戻ったとき、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はローカル変数の値を呼び出し元のコードの引数にコピーして戻す必要があります。  
  
 `ByRef` の引数の値がプロシージャにコピーされるとき、引数とパラメーターの型が同じであれば、変換は必要ありません。  しかし、型が異なる場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、双方向で変換を実行する必要があります。  どちらか一方が自分で定義したクラス型または構造体の型である場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はそれを他の型と双方向に変換する必要があります。  一方が拡張変換であれば、その逆の変換は縮小変換になる可能性があります。  
  
 **Error ID:** BC32053  
  
### このエラーを解決するには  
  
-   可能であれば、呼び出し元の引数にプロシージャのパラメーターと同じ型を使用します。そうすれば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は変換を行う必要がありません。  
  
-   パラメーターの型と異なる型の引数を指定してプロシージャを呼び出す必要があるが、値を呼び出し元の引数に戻す必要がない場合は、パラメーターを `ByRef` ではなく [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) で定義します。  
  
-   呼び出し元の引数に値を戻す必要がある場合は、可能であれば逆変換演算子を[Widening](../../../visual-basic/language-reference/modifiers/widening.md) で定義します。  
  
## 参照  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)