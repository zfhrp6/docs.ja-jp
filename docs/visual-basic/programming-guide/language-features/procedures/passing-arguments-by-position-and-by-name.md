---
title: "Passing Arguments by Position and by Name (Visual Basic) | Microsoft Docs"
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
  - "arguments [Visual Basic], passing by name"
  - "procedures, arguments"
  - ":= passing arguments"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "named arguments, passing arguments"
  - "arguments [Visual Basic], passing by position"
  - "Function procedures, passing arguments"
  - "named parameters, passing arguments"
  - "named arguments"
  - "passing parameters, named parameter arguments"
  - "passing parameters, by position"
  - "procedures, calling"
  - "named parameters"
  - "Sub procedures, passing arguments"
  - "argument passing"
  - "passing parameters, by name"
  - "argument passing, by position"
  - "arguments [Visual Basic], listing by name"
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Passing Arguments by Position and by Name (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Sub` プロシージャまたは `Function` プロシージャを呼び出すときには、引数を*位置で*渡したり*名前で*渡したりできます。位置で渡す場合は、プロシージャの定義で宣言されている順に引数を指定します。名前で渡す場合は、指定する位置 \(順序\) は関係なくなります。  
  
 引数を名前で渡すときには、宣言されている引数の名前、コロンと等号 \(`:=`\)、引数の値という順に指定します。  引数はどのような順序でも指定できます。  
  
 たとえば、次の `Sub` プロシージャでは 3 つの引数を使用します。  
  
 [!code-vb[VbVbcnProcedures#41](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/passing-arguments-by-pos_1.vb)]  
  
 このプロシージャを呼び出すときには、引数を位置で指定することも、名前で指定することも、両方を一緒に使って指定することもできます。  
  
## 位置による引数渡し  
 引数を位置で渡してプロシージャ  `studentInfo`  を呼び出すには、次のようにコンマで区切って指定します。  
  
 [!code-vb[VbVbcnProcedures#42](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/passing-arguments-by-pos_2.vb)]  
  
 位置で指定する引数リストで省略可能な引数を省略する場合は、省略する引数の場所にコンマを置く必要があります。   `age`  引数を指定せずに  `studentInfo`  を呼び出す例を次に示します。  
  
 [!code-vb[VbVbcnProcedures#43](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/passing-arguments-by-pos_3.vb)]  
  
## 名前による引数渡し  
 引数を名前で渡してプロシージャ  `studentInfo`  を呼び出すこともできます。この場合も、次のようにコンマで区切って指定します。  
  
 [!code-vb[VbVbcnProcedures#44](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/passing-arguments-by-pos_4.vb)]  
  
## 位置と名前の両方による引数渡し  
 次に示す例のように、1 つのプロシージャ呼び出しで、位置と名前の両方を使って引数を指定することもできます。  
  
 [!code-vb[VbVbcnProcedures#45](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/passing-arguments-by-pos_5.vb)]  
  
 上の例では、引数 `age` が省略されていますが、 `birth` が名前で指定されているため、 `age` の場所にコンマを置く必要はありません。  
  
 位置と名前の両方を使って引数を指定する場合は、位置で指定する引数をすべて先に指定する必要があります。  いったん名前で引数を指定したら、残りの引数はすべて名前で指定する必要があります。  
  
## 名前による省略可能な引数の指定  
 名前による引数渡しは、省略可能な引数が複数あるプロシージャを呼び出す場合に便利です。  引数を名前で指定する場合は、省略する引数の位置を示すためのコンマは必要はありません。  また、引数を名前で指定すると、どの引数を渡してどの引数を省略したのかが把握しやすくなります。  
  
## 名前による引数渡しの制限事項  
 引数を名前で渡しても、必要な引数を省略することはできません。  省略できるのは、省略可能な引数だけです。  
  
 パラメーター配列を名前で渡すことはできません。  これは、プロシージャの呼び出し時に、パラメーター配列ではコンマで区切られた不特定多数の引数が指定されますが、コンパイラは複数の引数を 1 つの名前に関連付けることができないためです。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)