---
title: "^ 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "^_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "^ 演算子 [C#]"
  - "ビットごとの排他的 OR 演算子 [C#]"
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# ^ 演算子 (C# リファレンス)
二項 `^` 演算子は、整数型と `bool` に対してあらかじめ定義されています。  整数型の場合、`^` ではオペランドのビットごとの排他的 OR が計算されます。  `bool` オペランドの場合は、`^` によりオペランドの排他的論理和が計算されます。つまり、片方のオペランドが `true` の場合だけ結果が `true` になります。  
  
## 解説  
 `^` 演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  通常、整数型に対する演算は、列挙に対して適用されます。  
  
## 使用例  
 [!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#30)]  
  
 前の例の `0xf8 ^ 0x3f` では、次の 2 つのバイナリ値に対してビットごとの排他的 OR 演算を行います。これらは 16 進値の F8 と 3F に相当します。  
  
 `1111 1000`  
  
 `0011 1111`  
  
 排他的 OR の結果は `1100 0111` で、16 進数の C7 に相当します。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)