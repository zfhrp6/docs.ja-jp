---
title: "%= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "%=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "%= 代入演算子 (剰余代入) [C#]"
  - "剰余代入演算子 (%=) [C#]"
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# %= 演算子 (C# リファレンス)
剰余代入演算子。  
  
## 解説  
 次のような `%=` 代入演算子を使用する式があるとします。  
  
```  
x %= y  
```  
  
 上記のコードは、次のコードと同じです。  
  
```  
x = x % y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [% 演算子](../../../csharp/language-reference/operators/modulus-operator.md)は、除算後の剰余を計算するために数値型に対して組み込まれています。  
  
 `%=` 演算子は直接オーバーロードできませんが、[% 演算子](../../../csharp/language-reference/operators/modulus-operator.md)はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#4)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)