---
title: "Optional Parameters (Visual Basic) | Microsoft Docs"
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
  - "parameters, optional"
  - "Visual Basic code, procedures"
  - "procedures, optional arguments"
  - "optional arguments"
  - "named arguments, and optional arguments"
  - "optional parameters"
  - "Optional keyword, optional arguments"
  - "arguments [Visual Basic], optional"
  - "optional arguments, and named arguments"
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Optional Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロシージャのパラメーターを省略可能にすると、呼び出し時に引数を指定する必要がなくなります。  *省略可能なパラメーター* にするには、プロシージャ定義で `Optional` キーワードを使用します。  次の規則が適用されます。  
  
-   プロシージャ定義のすべての省略可能なパラメーターについて、既定値を指定する必要があります。  
  
-   省略可能なパラメーターの既定値には、定数式を指定する必要があります。  
  
-   プロシージャ定義で省略可能なパラメーターの後に続くパラメーターは、すべて省略可能であることが必要です。  
  
 次の構文は、省略可能なパラメーターを含むプロシージャ宣言を示しています。  
  
```  
Sub sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## 省略可能なパラメーターを使ったプロシージャ呼び出し  
 省略可能なパラメーターを使ってプロシージャを呼び出すときには、引数を指定するかどうかを選択できます。  引数を指定しない場合は、そのパラメーターに対して宣言されている既定値が使用されます。  
  
 引数リストで省略可能な引数を省略する場合は、コンマを続けて、省略する引数の位置を表します。  次の例では、1 番目と 4 番目の引数は指定されていますが、2 番目と 3 番目の引数は省略されています。  
  
```  
  
sub name(argument 1, , , argument 4)  
```  
  
 次の例では、`MsgBox` 関数を数回呼び出します。  `MsgBox` には、必須パラメーター 1 つと省略可能なパラメーターが 2 つあります。  
  
 `MsgBox` の最初の呼び出しでは、`MsgBox` で定義された順番で 3 つの引数を指定します。  2 番目の呼び出しでは、必須の引数だけを指定します。  3 番目と 4 番目の呼び出しでは、1 つ目と 3 つ目の引数を指定します。  3 番目の呼び出しでは引数を位置で指定し、4 番目の呼び出しでは引数を名前で指定します。  
  
 [!code-vb[VbVbcnProcedures#47](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## 省略可能な引数があるかどうかの確認  
 引数が省略されているのか、呼び出し元のコードで既定値が明示的に指定されているのかについて、プロシージャで実行時に検出することはできません。  この区別が必要な場合は、ありそうにない値を既定値に設定します。  次のプロシージャでは、省略可能なパラメーター  `office` を定義し、その既定値  `QJZ` をテストして、呼び出しの際にこの引数が省略されているかどうかを確認します。  
  
 [!code-vb[VbVbcnProcedures#46](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 省略可能なパラメーターが `String` などの参照型の場合は、`Nothing` を既定値として使用できます。ただし、`Nothing` が引数の値として使用されることが予想される場合を除きます。  
  
## 省略可能なパラメーターとオーバーロード  
 省略可能なパラメーターを持つプロシージャを定義するには、オーバーロードを使用する方法もあります。  省略可能なパラメーターが 1 つあるとすると、パラメーターを受け取る場合と受け取らない場合の、2 つのオーバーロードされたバージョンのプロシージャを定義できます。  この方法は、省略可能なパラメーターの数が増えるにつれて複雑になります。  しかし、それぞれの省略可能な引数が呼び出しプログラムによって指定されているかどうかを確実に把握できるという利点があります。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)