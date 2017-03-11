---
title: "| 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "|_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "| 演算子 [C#]"
  - "二項演算子 (|) [C#]"
  - "ビットごとの OR 演算子 [C#]"
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# | 演算子 (C# リファレンス)
Binary       `|`  演算子は、整数型と `bool` に対してあらかじめ定義されています。  整数型の場合、  `|`ではオペランドのビットごとの OR が計算されます。  `bool` オペランドの場合は、  `|` オペランドの論理 OR が計算されます。つまり、両方のオペランドが `false` の場合だけ結果が `false` になります。  
  
## 解説  
 ユーザー定義型で         `|` 演算子はオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#31)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)