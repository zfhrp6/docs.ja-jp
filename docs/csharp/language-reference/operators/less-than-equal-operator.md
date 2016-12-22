---
title: "&lt;= 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "<=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<= 演算子 [C#]"
  - "以下演算子 (<=) [C#]"
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;= 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

すべての数値型と列挙型では、"より小さいか等しい" 関係演算子 \(`<=`\) が定義されています。この演算子では、最初のオペランドが 2 番目のオペランドより小さいか等しい場合に `true` が返され、それ以外の場合は `false` が返されます。  
  
## 解説  
 `<=` 演算子はユーザー定義型でオーバーロードできます。  詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  `<=` をオーバーロードする場合は、[\>\=](../Topic/%3E=%20Operator%20\(C%23%20Reference\).md) もオーバーロードする必要があります。  通常、整数型に対する演算は、列挙に対して適用されます。  
  
## 使用例  
 [!CODE [csRefOperators#32](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#32)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)