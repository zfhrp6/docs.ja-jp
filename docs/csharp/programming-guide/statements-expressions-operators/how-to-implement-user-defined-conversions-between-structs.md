---
title: "方法 : 構造体間にユーザー定義の変換を実装する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ユーザー定義変換 [C#]"
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : 構造体間にユーザー定義の変換を実装する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

この例では、`RomanNumeral` と `BinaryNumeral` の 2 つの構造体が定義されていて、これらの構造体間の変換を示しています。  
  
## 使用例  
 [!code-cs[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## 信頼性の高いプログラミング  
  
-   前述の例の次のステートメントは、  
  
     [!code-cs[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     このステートメントは、`RomanNumeral` から `BinaryNumeral` への変換を実行します。  `RomanNumeral` から `BinaryNumeral` への直接変換はないため、`RomanNumeral` から `int` へ変換するためのキャストと、`int` から `BinaryNumeral` へ変換するためのキャストが使用されています。  
  
-   また、次のステートメントは、  
  
     [!code-cs[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     `BinaryNumeral` から `RomanNumeral` への変換を実行します。  `RomanNumeral` は `BinaryNumeral` からの暗黙の型変換を定義しているため、キャストは不要です。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)