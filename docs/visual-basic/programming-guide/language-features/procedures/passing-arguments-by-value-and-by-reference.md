---
title: "Passing Arguments by Value and by Reference (Visual Basic) | Microsoft Docs"
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
  - "passing arguments, by value or by reference"
  - "ByVal keyword, passing arguments by value"
  - "arguments [Visual Basic], passing by value or by reference"
  - "argument passing, by value or by reference"
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# Passing Arguments by Value and by Reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、*値渡し*または*参照渡し*で引数をプロシージャに渡すことができます。  これは*引渡し方法*と呼ばれ、引数の基となる、呼び出し元のコードのプログラミング要素をプロシージャが変更できるかどうかが決まります。  プロシージャの宣言では、[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) または [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) キーワードを指定することで、各パラメーターの引き渡し方法を決定します。  
  
## 違い  
 引数をプロシージャに渡す場合、2 つの引き渡し方法の違いに注意してください。  
  
-   基になるプログラミング要素が変更可能か変更不可能か  
  
-   引数自体が変更可能か変更不可能か  
  
-   引数が値渡しか参照渡しか  
  
-   引数のデータ型が値型か参照型か  
  
 詳細については、「[Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)」および「[Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)」を参照してください。  
  
## 引数渡しの方法の選択  
 各引数の引き渡し方法は慎重に決定してください。  
  
-   **保護**。  引数を渡す方法を選択するときに最も重要な基準となるのは、呼び出し元のコードの変数を変更できるようにするかどうかです。  `ByRef` で引数を渡す場合の利点は、プロシージャから呼び出し元のコードに引数を通じて値を返すことができるという点にあります。  一方、`ByVal` を使用する利点は、プロシージャによって変数が変更されるのを防ぐことができるという点にあります。  
  
-   **パフォーマンス**。  どちらの方法を使用するかによってコードのパフォーマンスが変わってきますが、その差は一般にごくわずかです。  ただし、値型を `ByVal` で渡す場合は例外です。  この場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、引数の内容がすべてコピーされます。  このため、構造体などの大きな値型では、`ByRef` で渡す方が効率的です。  
  
     参照型では、データへのポインターだけがコピーされます \(32 ビット プラットフォームでは 4 バイト、64 ビット プラットフォームでは 8 バイト\)。  したがって、パフォーマンスを損なうことなく、`String` 型や `Object` 型の引数を値で渡すことができます。  
  
## 引数渡しの方法の決定  
 プロシージャの宣言では、各パラメーターの引き渡し方法を指定します。  呼び出し元のコードは `ByVal` 機構をオーバーライドすることはできません。  
  
 パラメーターが `ByRef`で宣言されている場合は、呼び出し元のコードは `ByVal` の呼び出しで引数名をかっこで囲むことによって機構ができます。  詳細については、「[How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)」を参照してください。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の既定の設定では、値渡しで引数が渡されます。  
  
## 値渡しで引数を渡す場合  
  
-   引数の基になる呼び出し元のコード要素が変更不可能である場合は、これに対応するパラメーターは [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) で宣言します。  変更不可能な要素の値は、どのようなコードでも変更できません。  
  
-   基になる要素が変更可能であっても、プロシージャからはその値を変更できないようにするには、パラメーターを `ByVal` で宣言します。  変更可能な要素が値渡しされた場合、その値を変更できるのは呼び出し元のコードだけです。  
  
## 参照渡しで引数を渡す場合  
  
-   プロシージャが、呼び出し元のコード内にある基になる要素を変更する必要が本当にある場合、対応するパラメーターを [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) で宣言します。  
  
-   プロシージャが正しく実行されるかどうかが、呼び出し元のコード内の基になる要素を変更するプロシージャに依存する場合、パラメーターを `ByRef` で宣言します。  これを値渡しした場合、または、呼び出し元のコードが引数をかっこで囲んで `ByRef` の引き渡し方法をオーバーライドした場合、プロシージャは予期しない結果になることがあります。  
  
## 例  
  
### 説明  
 値渡しで引数を渡す場合と参照渡しで引数を渡す場合の例を次に示します。  プロシージャ `Calculate` には、`ByVal` パラメーターと `ByRef` パラメーターの両方があります。  このプロシージャのタスクは、指定された利率 \(`rate`\) と総額 \(`debt`\) に基づいて、`debt` の元の値に利率を適用して `debt` の新しい値を計算することです。  `debt` は `ByRef` パラメーターであるため、新しい総額は、`debt` に対応する呼び出し元コードの引数の値に反映されます。  `rate` の値は `Calculate` で変更されないため、このパラメーターは `ByVal` パラメーターです。  
  
### コード  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)