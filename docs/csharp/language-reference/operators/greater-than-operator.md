---
title: "&gt; 演算子 (C# リファレンス) | Microsoft Docs"
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
  - ">_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "> 演算子 [C#]"
  - "大なり演算子 (>) [C#]"
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &gt; 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

すべての数値型および列挙型では、"より大きい" 関係演算子 \(`>`\) が定義されています。この演算子では、最初のオペランドが 2 番目のオペランドより大きい場合に `true` が返され、それ以外の場合は `false` が返されます。  
  
## 解説  
 `>` 演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  `>` をオーバーロードする場合は、[\<](../Topic/%3C%20Operator%20\(C%23%20Reference\).md) もオーバーロードする必要があります。  二項演算子をオーバーロードすると、対応する代入演算子がある場合には、この演算子も暗黙でオーバーロードされます。  
  
## 使用例  
 [!CODE [csRefOperators#29](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#29)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)