---
title: "% 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "%_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "% 演算子 [C#]"
  - "剰余演算子 [C#]"
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# % 演算子 (C# リファレンス)
`%` 演算子は、秒までに 1 番目のオペランドで除算された後の剰余を計算します。  すべての数値型は剰余演算子があります。  
  
## 解説  
 `%` 演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  二項演算子をオーバーロードすると、対応する代入演算子がある場合には、この演算子も暗黙でオーバーロードされます。  
  
## 使用例  
 [!code-cs[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#9)]  
  
## コメント  
 double 型では丸め誤差が発生することに注意してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)