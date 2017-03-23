---
title: "&gt;= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - ">=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ">= 演算子 [C#]"
  - "以上演算子 (>=) [C#]"
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# &gt;= 演算子 (C# リファレンス)
すべての数値型および列挙型では、"より大きいか等しい" 関係演算子 \(`>=`\) が定義されています。この演算子では、最初のオペランドが 2 番目のオペランドより大きいか等しい場合に `true` が返され、それ以外の場合は `false` が返されます。  
  
## 解説  
 `>=` 演算子はユーザー定義型でオーバーロードできます。  詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  `>=` をオーバーロードする場合は、[\<\=](../../../csharp/language-reference/operators/less-than-equal-operator.md) もオーバーロードする必要があります。  通常、整数型に対する演算は、列挙に対して適用されます。  
  
## 使用例  
 [!code-cs[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)