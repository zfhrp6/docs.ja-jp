---
title: "Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;, =, &lt;&gt;, &lt;, &lt;=, &gt;, &gt;=, CType, IsTrue, IsFalse | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33000"
  - "vbc33000"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC33000"
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;, =, &lt;&gt;, &lt;, &lt;=, &gt;, &gt;=, CType, IsTrue, IsFalse
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣言できる演算子は、オーバーロード可能な演算子のみです。  宣言できる演算子を次の表に示します。  
  
|種類|演算子|  
|--------|---------|  
|単項式|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|変換 \(単項\)|`CType`|  
  
 二項演算の一覧に示した `=` 演算子は、代入演算子ではなく比較演算子です。  
  
 **Error ID:** BC33000  
  
### このエラーを解決するには  
  
1.  演算子をオーバーロード可能なものの中から選択します。  
  
2.  直接オーバーロードできない演算子をオーバーロードした機能が必要な場合は、適切なパラメーターを受け取って適切な値を返す `Function` プロシージャを作成します。  
  
## 参照  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)