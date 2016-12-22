---
title: "Differences Between Parameters and Arguments (Visual Basic) | Microsoft Docs"
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
  - "procedures, parameters"
  - "parameters, and arguments"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], and parameters"
  - "procedure parameters"
  - "parameters, definition"
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Parameters and Arguments (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロシージャは、ほとんどの場合、呼び出されたときの状況に関する情報を必要とします。  繰り返し実行されるタスクや共有されているタスクを実行するプロシージャは、呼び出されるたびに異なる情報を使用します。  この情報は、プロシージャを呼び出すときに渡される変数、定数、および式から構成されています。  
  
 この情報をプロシージャに渡すために、プロシージャには*パラメーター*が定義され、呼び出し元のコードはそのパラメーターに*引数*を渡します。  パラメーターは駐車場、引数は自動車であると考えてみてください。  駐車場にはさまざまな車が駐車できるのと同様に、呼び出し元のコードは、パラメーターを呼び出すたびに、同じパラメーターに別の引数を渡すことができます。  
  
## パラメーター  
 *パラメーター*は、プロシージャが呼び出されるときに期待する値を表します。  パラメーターは、プロシージャの宣言で定義されます。  
  
 `Function` または `Sub` プロシージャを定義するときは、プロシージャ名のすぐ後に、かっこで囲んだ*パラメーター リスト*を指定します。  各パラメーターには、名前、データ型、引き渡し方法 \([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) または [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)\) を指定します。  パラメーターが省略可能であることを示すこともできます。  これは、呼び出し元のコードがその値を渡す必要がないということを意味します。  
  
 各パラメーターの名前は、プロシージャ内で*ローカル変数*として扱われます。  パラメーター名は、他の変数と同じように使用できます。  
  
## 引数  
 *引数*は、プロシージャを呼び出すときに、プロシージャのパラメーターに渡す値を表します。  呼び出し元のコードは、プロシージャを呼び出すときに引数を渡します。  
  
 `Function` または `Sub` プロシージャを定義するときは、プロシージャ名のすぐ後にかっこで囲んだ*引数リスト*を含めます。  リスト内の各引数は、パラメーター リスト内の同じ位置にあるパラメーターに対応します。  
  
 パラメーターの定義とは異なり、引数には名前がありません。  引数は式で、0 以上の変数、定数、リテラルを含めることができます。  評価済みの式のデータ型は、通常は、対応するパラメーターに定義されたデータ型と一致します。それ以外の場合でも、パラメーターのデータ型と互換性がある必要があります。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Parameter for a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)