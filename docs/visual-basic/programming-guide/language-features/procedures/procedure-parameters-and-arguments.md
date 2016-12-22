---
title: "Procedure Parameters and Arguments (Visual Basic) | Microsoft Docs"
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
  - "procedures, argument lists"
  - "values, passing to procedures"
  - "arguments [Visual Basic], passing"
  - "procedures, parameters"
  - "Visual Basic code, argument lists"
  - "Visual Basic code, procedures"
  - "parameters, Visual Basic procedures"
  - "parameters, lists"
  - "arguments [Visual Basic], Visual Basic procedures"
  - "arguments [Visual Basic], procedures"
  - "parameter lists"
  - "Visual Basic code, parameter lists"
  - "argument lists"
  - "procedures, parameter lists"
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedure Parameters and Arguments (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロシージャは、ほとんどの場合、呼び出されたときの状況に関する情報を必要とします。  繰り返し実行されるタスクや共有されているタスクを実行するプロシージャは、呼び出されるたびに異なる情報を使用します。  この情報は、プロシージャを呼び出すときに渡される変数、定数、および式から構成されています。  
  
 *パラメーター*は、プロシージャが呼び出されるときに期待する値を表します。  パラメーターは、プロシージャの宣言で定義されます。  
  
 プロシージャは、パラメーターなしでも、1 つのパラメーターでも、複数のパラメーターでも定義できます。  プロシージャの定義のうち、パラメーターを指定する部分を*パラメーター リスト*と呼びます。  
  
 *引数*は、プロシージャを呼び出すときに、プロシージャのパラメーターに渡す値を表します。  呼び出し元のコードは、プロシージャを呼び出すときに引数を渡します。  プロシージャ呼び出しのうち、引数を指定する部分を*引数リスト*と呼びます。  
  
 次の図は、プロシージャ `safeSquareRoot` を 2 つの場所から呼び出すコードを示したものです。  最初の呼び出しでは、変数 `x` の値 \(4.0\) をパラメーター `number` に渡し、`root` の戻り値 \(2.0\) が変数 `y` に代入されます。  2 番目の呼び出しでは、リテラル値 9.0 を `number` に渡し、戻り値 \(3.0\) を変数 `z` に代入します。  
  
 ![パラメーターに引数を渡すグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/procedures/media/parametersargue.gif "ParametersArgue")  
パラメーターに引数を渡す  
  
 詳細については、「[Differences Between Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)」を参照してください。  
  
## パラメーターのデータ型  
 パラメーターのデータ型を宣言するには、パラメーターの宣言の中で `As` 句を使用します。  たとえば、次の関数は、文字列型と整数型の引数を受け取ります。  
  
 [!code-vb[VbVbcnProcedures#32](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 型チェック スイッチ \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) が `Off,` の場合、`As` 句は省略可能です。ただし、いずれかのパラメーターがこれを使用している場合は、すべてのパラメーターで使用する必要があります。  型チェックが `On` になっている場合は、プロシージャのすべての引数に `As` 句が必要です。  
  
 `String` パラメーターに `Byte` を渡すなど、呼び出し元のコードが、対応するパラメーターとは異なるデータ型の引数を渡す場合、次のいずれかの作業が必要です。  
  
-   パラメーターのデータ型に拡大変換されるデータ型の引数だけを渡す  
  
-   暗黙の縮小変換を許可する `Option Strict Off` を設定する  
  
-   変換キーワードを使用してデータ型を明示的に変換する  
  
### 型パラメーター。  
 *ジェネリック プロシージャ* も、通常のパラメーターの他に 1 つ以上の*型パラメーター*を定義します。  ジェネリック プロシージャを使うと、呼び出し元のコードは、プロシージャを呼び出すたびに異なるデータ型を渡すことができるため、個々の呼び出しの要件に合わせてデータ型を変更できます。  [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) を参照してください。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Parameter for a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)