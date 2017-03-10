---
title: "Parameter Arrays (Visual Basic) | Microsoft Docs"
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
  - "parameter arrays, about parameter arrays"
  - "ParamArray keyword, parameter arrays"
  - "Visual Basic code, procedures"
  - "parameters, parameter arrays"
  - "arguments [Visual Basic], parameter arrays"
  - "procedures, indefinite number of argument values"
  - "arrays [Visual Basic], parameter arrays"
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Parameter Arrays (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

通常は、プロシージャ宣言で指定されているより多くの引数を使ってプロシージャを呼び出すことはできません。  不特定多数の引数が必要な場合は、*パラメーター配列*を宣言すると、値の配列をプロシージャのパラメーターとして渡すことができます。  プロシージャを定義するときには、パラメーター配列の要素の数がわからなくてもかまいません。  配列のサイズは、プロシージャの呼び出しごとに個別に決定されます。  
  
## ParamArray を宣言する  
 パラメーター リストでパラメーター配列を指定するには、[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) キーワードを使用します。  次の規則が適用されます。  
  
-   プロシージャはパラメーター配列を 1 つだけ定義でき、これはプロシージャの定義の最後のパラメーターである必要があります。  
  
-   パラメーター配列は値渡しで渡す必要があります。  プロシージャ定義で [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) キーワードを使って明示的に指定することをお勧めします。  
  
-   パラメーター配列は自動的に省略可能になります。  既定値は、パラメーター配列の要素型の空の 1 次元配列です。  
  
-   パラメーター配列より前には、必須のパラメーターだけを指定します。  省略可能なパラメーターはパラメーター配列だけであることが必要です。  
  
## ParamArray を呼び出す  
 パラメーター配列を定義するプロシージャを呼び出す場合、引数は次のいずれかの方法で渡します。  
  
-   なし。[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 引数は省略できます。  この場合は、空の配列がプロシージャに渡されます。  [Nothing](../../../../visual-basic/language-reference/nothing.md) キーワードを渡しても同じ結果になります。  
  
-   コンマで区切った任意の数の引数のリスト。  各引数のデータ型は、暗黙的に `ParamArray` 要素型に変換できる必要があります。  
  
-   パラメーター配列と同じ要素型の配列  
  
 いずれの場合も、プロシージャ内のコードでは、各要素が `ParamArray` データ型と同じデータ型の 1 次元配列として、パラメーター配列を扱う必要があります。  
  
> [!IMPORTANT]
>  無限に増大する配列を扱う場合、アプリケーション内部の容量を超過してしまう可能性があります。  パラメーター配列を受け取る場合は、呼び出し元のコードが渡した配列のサイズをテストする必要があります。  このサイズがアプリケーションには大きすぎる場合、適切な手順を行う必要があります。  詳細については、「[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)」を参照してください。  
  
## 例  
 次の例では、関数 `calcSum`を定義し、ダイヤルいます。  パラメーター `args` の `ParamArray` の修飾子は可変数の引数を使用すると、関数ができます。  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/parameter-arrays_1.vb)]  
  
 パラメーター配列を受け取るプロシージャを定義し、パラメーター配列に渡されたすべての要素の値を出力する例を次に示します。  
  
 [!code-vb[VbVbcnProcedures#48](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/parameter-arrays_3.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)