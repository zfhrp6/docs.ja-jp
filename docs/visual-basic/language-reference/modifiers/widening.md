---
title: "Widening (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.widening"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversions, type"
  - "type conversion"
  - "conversions, data type"
  - "Widening keyword"
  - "data type conversion"
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Widening (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変換演算子 \(`CType`\) がクラスまたは構造体を、元の型に格納可能なすべての値を格納できる型に変換することを指定します。  
  
## Widening キーワードによる変換  
 変換プロシージャには、`Widening` の他に `Public Shared` を指定する必要があります。  
  
 拡大変換は、実行時には常に正常に行われ、データ消失が発生することはありません。  `Single` から `Double`、`Char` から `String`、または派生型から基本型への変換などが例として挙げられます。  最後の例が拡大変換なのは、派生型には基本型のすべてのメンバーが含まれ、したがって基本型のインスタンスについても同様だからです。  
  
 コードでは `Option Strict` が `On` の場合でも、拡大変換に `CType` を使う必要はありません。  
  
 `Widening` キーワードは、次のコンテキストで使用します。  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 拡大変換演算子と縮小変換演算子の定義の例については、「[How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)」を参照してください。  
  
## 参照  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)