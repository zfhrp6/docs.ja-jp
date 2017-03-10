---
title: "&amp; 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "&_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ビットごとの AND 演算子 [C#]"
  - "アンパサンド演算子 (&) [C#]"
  - "& 演算子 [C#]"
  - "AND 演算子 (&) [C#]"
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# &amp; 演算子 (C# リファレンス)
& 演算子は、単項演算子または二項演算子として機能します。  
  
## 解説  
 単項 & 演算子では、オペランドのアドレスが返されます \([unsafe](../../../csharp/language-reference/keywords/unsafe.md)コンテキストが必要\)。  
  
 二項 & 演算子は、整数型と `bool` に対してあらかじめ定義されています。  整数型の場合、& はオペランドのビットごとの論理 AND を計算します。  `bool` オペランドの場合は、オペランドの論理 AND が計算されます。つまり、両方のオペランドが `true` の場合だけ結果が `true` になります。  
  
 `&` 演算子は、1 番目の演算子の値に関係なく、両方の演算子を評価します。  次に例を示します。  
  
 [!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#37)]  
  
 二項 `&` 演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  通常、整数型に対する演算は、列挙に対して適用されます。  二項演算子をオーバーロードすると、対応する代入演算子がある場合には、この演算子も暗黙でオーバーロードされます。  
  
## 使用例  
 [!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#38)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)