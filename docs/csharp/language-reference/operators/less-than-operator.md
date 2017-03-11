---
title: "&lt; 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "< 演算子 [C#]"
  - "小なり演算子 (<) [C#]"
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# &lt; 演算子 (C# リファレンス)
すべての数値型と列挙型では、"より小さい" 関係演算子 \(`<`\) が定義されています。この演算子では、最初のオペランドが 2 番目のオペランドより小さい場合に `true` が返され、それ以外の場合は `false` が返されます。  
  
## 解説  
 `<` 演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  `<` をオーバーロードする場合は、[\>](../../../csharp/language-reference/operators/greater-than-operator.md) もオーバーロードする必要があります。  二項演算子をオーバーロードすると、対応する代入演算子がある場合には、この演算子も暗黙でオーバーロードされます。  
  
## 使用例  
 [!code-cs[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#24)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)