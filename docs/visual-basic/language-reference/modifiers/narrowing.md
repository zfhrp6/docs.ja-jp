---
title: "Narrowing (Visual Basic) | Microsoft Docs"
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
  - "vb.narrowing"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversions, type"
  - "type conversion"
  - "conversions, data type"
  - "Narrowing keyword"
  - "data type conversion"
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Narrowing (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

変換演算子 \(`CType`\) が、元のクラスまたは構造体の値を格納しきれないデータ型にクラスまたは構造体を変換することを示します。  
  
## Narrowing キーワードを使用した変換  
 変換のプロシージャでは、`Narrowing` に加えて `Public Shared` を指定する必要があります。  
  
 縮小変換は、実行時に常に正しく実行されるとは限りません。したがって失敗またはデータを消失する可能性があります。  たとえば、`Long` から `Integer`、`String` から `Date`、基本型から派生型への変換などです。  基本型から派生型への変換が縮小変換なのは、基本型には派生型のすべてのメンバーが含まれていない場合があり、派生型のインスタンスではないためです。  
  
 `Option Strict` が `On` の場合、コードではすべての縮小変換に `CType` を使用する必要があります。  
  
 キーワード `Narrowing` は、次の構文で使用します。  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## 参照  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)