---
title: "/= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/= (除算代入演算子) [C#]"
  - "除算代入演算子 (/=) [C#]"
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# /= 演算子 (C# リファレンス)
除算代入演算子です。  
  
## 解説  
 次のような `/=` 代入演算子を使用する式があるとします。  
  
```  
x /= y  
```  
  
 上記のコードは、次のコードと同じです。  
  
```  
x = x / y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [\/ 演算子](../../../csharp/language-reference/operators/division-operator.md)は、除算のために数値型に対して組み込まれています。  
  
 `/=` 演算子は直接オーバーロードできませんが、[\/ 演算子](../../../csharp/language-reference/operators/division-operator.md)はユーザー定義型でオーバーロードできます。詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  すべての複合代入演算子において、二項演算子をオーバーロードすると、同等の複合代入が暗黙的にオーバーロードされます。  
  
## 使用例  
 [!code-cs[csRefOperators#5](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#5)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)