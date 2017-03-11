---
title: "- 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "-_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "- 演算子 [C#]"
  - "減算演算子 (-) [C#]"
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# - 演算子 (C# リファレンス)
`-` 演算子は、単項演算子または二項演算子として機能します。  
  
## 解説  
 単項 `-` 演算子は、すべての数値型に対してあらかじめ定義されています。  数値型での単項 `-` 演算子の結果は、オペランドの符号を反転した数値になります。  
  
 二項 `-` 演算子は、すべての数値型と列挙型に対して組み込まれています。二項 \- 演算子では、最初のオペランドから 2 番目のオペランドが減算されます。  
  
 デリゲート型でも、デリゲートを削除する二項 `-` 演算子が用意されています。  
  
 単項 `-` 演算子と二項 `-` 演算子は、ユーザー定義型でオーバーロードできます。  詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#40)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)