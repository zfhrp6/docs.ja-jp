---
title: "+ 演算子 (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "+_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "+ 演算子 [C#]"
  - "加算演算子 [C#]"
  - "連結演算子 [C#]"
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# + 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`+` 演算子は、単項演算子または二項演算子として機能します。  
  
## 解説  
 単項 `+` 演算子は、すべての数値型に対してあらかじめ定義されています。  数値型での単項 `+` 演算の結果は、単にオペランドの値になります。  
  
 二項 `+` 演算子は、数値型と文字列型に対してあらかじめ定義されています。  数値型の場合、\+ は 2 つのオペランドの合計を計算します。  オペランドの片方または両方が文字列型の場合は、オペランドの文字列表現が連結されます。  
  
 デリゲート型でも、デリゲートを連結する二項 `+` 演算子が用意されています。  
  
 単項 `+` 演算子と二項 `+` 演算子は、ユーザー定義型でオーバーロードできます。  通常、整数型に対する演算は、列挙に対して適用されます。  詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!CODE [csRefOperators#28](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#28)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)