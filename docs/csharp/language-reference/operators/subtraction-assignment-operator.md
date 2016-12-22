---
title: "/= 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "/=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/= (除算代入演算子) [C#]"
  - "除算代入演算子 (/=) [C#]"
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /= 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
 [!CODE [csRefOperators#5](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#5)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)