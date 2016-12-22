---
title: "How to: Change the Value of a Procedure Argument (Visual Basic) | Microsoft Docs"
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
  - "arguments [Visual Basic], ByRef"
  - "arguments [Visual Basic], changing value"
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Change the Value of a Procedure Argument (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロシージャを呼び出すときに指定する各引数は、プロシージャに定義されたパラメーターのいずれかに対応します。  場合によっては、プロシージャのコードで、呼び出し元のコードにある引数の基の値が変更されることもあります。  または、引数のローカル コピーだけがプロシージャで変更される場合もあります。  
  
 プロシージャを呼び出すと、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) で渡されたすべての引数のローカル コピーを作成します。  [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) で渡された各引数に対しては、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] により、プロシージャ コードから呼び出し元のコードにある引数の基のプログラミング要素を直接参照できるように設定されます。  
  
 呼び出し元のコードにある基の要素が可変であり、引数が `ByRef` で渡されていれば、プロシージャ コードから呼び出し元のコードにある要素の値を直接参照して変更できます。  
  
## 基の値を変更する  
  
#### 呼び出し元のコードにある、プロシージャ引数の基の値を変更するには  
  
1.  プロシージャ宣言で、引数に対応するパラメーターに [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) を指定します。  
  
2.  呼び出し元のコードで、可変のプログラミング要素を引数として渡します。  
  
3.  呼び出し元のコードで、引数を引数リストのかっこで囲まないでください。  
  
4.  プロシージャ コードでパラメーター名を使用して、呼び出し元のコードにある基の要素に値を代入します。  
  
 詳しくは、後に示すコード例を参照してください。  
  
## ローカル コピーの変更  
 呼び出し元のコードにある基の要素が不変であるか、または引数が `ByVal` で渡されている場合、プロシージャから呼び出し元のコードにある基の値を変更できません。  ただし、プロシージャからこの引数のローカル コピーを変更できます。  
  
#### プロシージャ コードにある、プロシージャ引数のコピーを変更するには  
  
1.  プロシージャ宣言で、引数に対応するパラメーターに [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) を指定します。  
  
     または  
  
     呼び出し元のコードで、引数を引数リストのかっこで囲みます。  こうすると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は引数に対応するパラメーターに `ByRef` が指定されている場合でも、引数を値渡しで渡します。  
  
2.  プロシージャ コードでパラメーター名を使用して、引数のローカル コピーに値を代入します。  呼び出し元のコードにある基の値は変更されません。  
  
## 使用例  
 次の例には、配列変数を受け取ってその要素を操作する 2 つのプロシージャがあります。  `increase` プロシージャは、各要素に単純に 1 を加算します。  `replace` プロシージャは、新しい配列をパラメーター `a()` 煮割り当て、各要素に 1 を加算します。  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 最初の `MsgBox` の呼び出しでは、"After increase\(n\): 11, 21, 31, 41" と表示されます。  配列  `n`  は参照型なので、引き渡し方法が `ByVal` でも、 `replace`  によってこのメンバーを変更できます。  
  
 2 度目に `MsgBox` を呼び出すと、"After replace\(n\): 101, 201, 301" が表示されます。  `n` が `ByRef` で渡されたため、 `replace` から呼び出し元のコードにある変数 `n` を変更でき、新しい配列を変数に代入できます。   `n` が参照型なので、 `replace` からそのメンバーを変更することもできます。  
  
 プロシージャから呼び出し元のコードにある変数そのものを変更しないようにできます。  「[How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)」を参照してください。  
  
## コードのコンパイル  
 参照渡しで変数を渡すときには、`ByRef` キーワードを使って明示的に指定する必要があります。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の既定の設定では、値渡しで引数が渡されます。  ただし、パラメーターを宣言するときには、[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) または [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) のどちらかのキーワードを常に含めるようにすることをお勧めします。  これによって、コードが読みやすくなります。  
  
## .NET Framework セキュリティ  
 呼び出し元のコードにある引数の基の値をプロシージャから変更できるようにすると、必ず危険が伴います。  変更すべき値が変更されていることを確認し、検証用のコードを作成して値を使用する前にチェックしてください。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)