---
title: "How to: Protect a Procedure Argument Against Value Changes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "arguments [Visual Basic], passing by reference"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], ByVal"
  - "arguments [Visual Basic], passing by value"
  - "procedure parameters"
  - "procedures, calling"
  - "arguments [Visual Basic], ByRef"
  - "arguments [Visual Basic], changing value"
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Protect a Procedure Argument Against Value Changes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロシージャがパラメーターを [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) で宣言すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はプロシージャ コードに、呼び出し元のコードの引数の基となるプログラミング要素への直接の参照を追加します。  これにより、プロシージャが呼び出し元のコードの引数の基となる値を変更できます。  場合によっては、呼び出し元のコードがこのような変更を禁止する場合もあります。  
  
 引数が変更されるのを防ぐには、プロシージャ内で、対応するパラメーターを [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) で宣言します。  特定の引数を、特定の場合のみ変更するには、この引数を `ByRef` で宣言し、呼び出し元のコードが、呼び出しのたびに引き渡し方法を決定できるようにします。  対応する引数をかっこで囲むと値で渡され、かっこで囲まないと参照が渡されます。  詳細については、「[How to: Force an Argument to Be Passed by Value](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)」を参照してください。  
  
## 使用例  
 次の例には、配列変数を受け取ってその要素を操作する 2 つのプロシージャがあります。  `increase` プロシージャは、各要素に単純に 1 を加算します。  `replace` プロシージャは、新しい配列をパラメーター `a()` 煮割り当て、各要素に 1 を加算します。  ただし、この新しい配列の代入は、呼び出し元のコードの基の配列変数には反映されません。  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 最初の `MsgBox` の呼び出しでは、"After increase\(n\): 11, 21, 31, 41" と表示されます。  配列  `n`  は参照型なので、引き渡し方法が `ByVal` でも、 `replace`  によってこのメンバーを変更できます。  
  
 2 番目の `MsgBox` の呼び出しでは、"After replace\(n\): 11, 21, 31, 41" と表示されます。   `n`  は `ByVal` で渡されるので、 `replace`  は呼び出し元のコードで新しい配列を割り当てても変数  `n`  を変更できません。   `replace`  が新しい配列インスタンス  `k`  を作成して、これをローカル変数  `a` に割り当てた場合、呼び出し元のコードが渡した  `n`  への参照は失われます。   `a` のメンバーを変更すると、ローカル配列  `k`  のみが影響を受けます。  したがって、 `replace`  は、呼び出し元のコードにある配列  `n`  の値をインクリメントしません。  
  
## コードのコンパイル  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の既定の設定では、値渡しで引数が渡されます。  ただし、パラメーターを宣言するときには、[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) または [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) のどちらかのキーワードを常に含めるようにすることをお勧めします。  これによって、コードが読みやすくなります。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Force an Argument to Be Passed by Value](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)