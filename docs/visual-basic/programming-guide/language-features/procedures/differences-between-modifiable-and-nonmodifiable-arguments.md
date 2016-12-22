---
title: "Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic) | Microsoft Docs"
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
  - "procedures, arguments"
  - "procedure arguments"
  - "arguments [Visual Basic], nonmodifiable"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], modifiable"
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロシージャを呼び出すとき、通常はいくつかの引数を渡します。  各引数は、基底にあるプログラミング要素に対応します。  基底にある要素と引数の両方が、変更できる場合とできない場合があります。  
  
## 変更できる要素と変更できない要素  
 プログラミング要素は、値を変更できる「*変更できる要素*」と、作成時から値が変更されない「*変更できない要素*」の 2 つに分けられます。  
  
 次の表に、変更できるプログラミング要素と変更できないプログラミング要素を挙げます。  
  
|変更できる要素|変更できない要素|  
|-------------|--------------|  
|オブジェクト変数を含むローカル変数 \(プロシージャ内で宣言されたもの\) 読み取り専用を除く|読み取り専用変数、フィールド、プロパティ|  
|フィールド \(モジュール、クラス、構造体のメンバー変数\) 読み取り専用を除く|定数とリテラル|  
|プロパティ、読み取り専用を除く|列挙型メンバー|  
|配列要素|式 \(式内の要素が変更可能な場合も\)|  
  
## 変更できる引数と変更できない引数  
 *変更できる引数*は、基底にある要素が変更できるものです。  呼び出し元のコードは、いつでも新しい値を格納でき、引数 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) を渡すと、プロシージャ内のコードが、呼び出し元のコードにある基底の要素を変更できます。  
  
 *変更できない引数*は、変更できない要素が基底にあるか、[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) で渡されています。  呼び出し元のコードの基底の要素が変更可能な要素であっても、プロシージャはこれを変更できません。  基底の要素が変更できない要素である場合、呼び出し元のコード自身もこれを変更できません。  
  
 呼び出したプロシージャによって変更できない引数のコピーが変更されることはあっても、その変更が呼び出し元のコードの基の要素に影響することはありません。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)