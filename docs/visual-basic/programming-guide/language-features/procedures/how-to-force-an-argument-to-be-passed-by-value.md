---
title: "How to: Force an Argument to Be Passed by Value (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], ByVal"
  - "arguments [Visual Basic], passing by value"
  - "procedure parameters"
  - "procedures, calling"
  - "arguments [Visual Basic], in parentheses"
  - "procedure arguments, in parentheses"
  - "arguments [Visual Basic], changing value"
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Force an Argument to Be Passed by Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

引数を渡す方法は、プロシージャの宣言によって決まります。  パラメーターが [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) で宣言されている場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は対応する引数が参照渡しで渡されると予測します。  この場合、プロシージャは呼び出し元のコードにある引数の基のプログラミング要素の値を変更できます。  基の要素をこの方法で変更しないように保護する場合は、プロシージャの呼び出し時に引数名をかっこで囲むことによって、`ByRef` の引数渡しの方法をオーバーライドします。  このかっこは、呼び出し時に引数リストを囲むかっこに追加して記述します。  
  
 呼び出し元のコードで [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) の引数渡しの方法をオーバーライドすることはできません。  
  
### 引数の値渡しを強制するには  
  
-   プロシージャ内で対応するパラメーターが `ByVal` として宣言されている場合は、それ以上何もする必要はありません。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、引数が値渡しで渡されることを既に予期しています。  
  
-   プロシージャ内で対応するパラメーターが `ByRef` で宣言されている場合は、プロシージャの呼び出し時に引数をかっこで囲みます。  
  
## 使用例  
 `ByRef` のパラメーター宣言をオーバーライドする例を次に示します。  `ByVal` を強制している呼び出しの部分で、かっこが二重に記述されている点に注意してください。  
  
 [!code-vb[VbVbcnProcedures#39](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-force-an-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-force-an-argument_2.vb)]  
  
 引数リストの内部で `str` が二重のかっこに囲まれると、`setNewString` プロシージャは呼び出し元のコードにあるその値を変更できず、`MsgBox` に "Cannot be replaced if passed ByVal" と表示します。  `str` が二重のかっこで囲まれなければ、プロシージャは値を変更でき、`MsgBox` には "This is a new value for the inString argument" と表示されます。  
  
## コードのコンパイル  
 参照渡しで変数を渡すときには、`ByRef` キーワードを使って明示的に指定する必要があります。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の既定の設定では、値渡しで引数が渡されます。  ただし、パラメーターを宣言するときには、[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) または [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) のどちらかのキーワードを常に含めるようにすることをお勧めします。  これによって、コードが読みやすくなります。  
  
## 信頼性の高いプログラミング  
 プロシージャにパラメーターが [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) で宣言されている場合、そのコードを正しく実行できるかどうかは、呼び出し元のコードにある基の要素を変更できるかどうかに左右されます。  呼び出し元のコードで引数をかっこで囲むことによって、この引数渡しの方法がオーバーライドされた場合、または変更不可能な引数が渡された場合は、プロシージャから基の要素を変更できません。  これによって、呼び出し元のコードで予期しない結果になる場合があります。  
  
## .NET Framework セキュリティ  
 呼び出し元のコードにある引数の基の値をプロシージャから変更できるようにすると、必ず危険が伴います。  変更すべき値が変更されていることを確認し、検証用のコードを作成して値を使用する前にチェックしてください。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)