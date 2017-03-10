---
title: "Differences Between Passing an Argument By Value and By Reference (Visual Basic) | Microsoft Docs"
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
  - "ByRef keyword, passing arguments by reference"
  - "Visual Basic code, procedures"
  - "procedures, passing arguments"
  - "ByVal keyword, passing arguments by value"
  - "arguments [Visual Basic], passing by value or by reference"
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Differences Between Passing an Argument By Value and By Reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャに 1 つ以上の引数を渡す場合、各引数は呼び出し元のコードにある基のプログラミング要素に対応付けられます。  この基になる要素の値を渡すこともあれば、要素への参照を渡すこともあります。  これを、*値渡しと参照渡し*と呼びます。  
  
## 値渡し  
 引数を*値渡し*で渡すには、プロシージャ定義内で対応するパラメーターに [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) キーワードを指定します。  値渡しを使用すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は基になるプログラミング要素の値をプロシージャ内のローカル変数にコピーします。  プロシージャ コードから呼び出し元のコードにある基の要素にアクセスすることはできません。  
  
## 参照渡し  
 引数を*参照渡し*で渡すには、プロシージャ定義内で対応するパラメーターに [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) キーワードを指定します。  参照渡しを使用すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は呼び出し元のコードにある基のプログラミング要素を、プロシージャから直接参照できるようにします。  
  
## 引数渡しの方法と要素の型  
 値渡しと参照渡しのどちらを選ぶかは、基になる要素の型に応じて決めるわけではありません。  値渡しか参照渡しかによって、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] がプロシージャ コードに何を提供するかが変わります。  一方、値型か参照型かによって、プログラミング要素がメモリにどのように格納されるかが変わります。  
  
 しかし、値渡し\/参照渡しと要素の型は無関係ではありません。  参照型の値は、メモリ内の他の場所にあるデータへのポインターです。  つまり、参照型を値渡しで渡すと、プロシージャ コードは基の要素自体にはアクセスできませんが、基の要素のデータをポイントできるようになります。  たとえば、要素が配列変数であった場合、プロシージャ コードは変数そのものにはアクセスできませんが、配列のメンバーにはアクセスできます。  
  
## 要素の変更  
 不変要素を引数として渡す場合、`ByVal` と `ByRef` のどちらを使用するかに関係なく、プロシージャは呼び出し元のコードにある要素を変更できません。  
  
 可変要素の場合の要素のデータ型と引数渡しの方法との関係を次の表に示します。  
  
|要素の型|`ByVal` で渡す場合|`ByRef` で渡す場合|  
|----------|-------------------|-------------------|  
|値型 \(格納されるのは値のみ\)|プロシージャは、変数およびそのメンバーを一切変更できません。|プロシージャは、変数およびそのメンバーを変更できます。|  
|参照型 \(クラスまたは構造体のインスタンスへのポインターを格納\)|プロシージャは、変数を変更することはできませんが、変数が指すインスタンスのメンバーを変更できます。|プロシージャは、変数および変数が指すインスタンスのメンバーを変更できます。|  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)