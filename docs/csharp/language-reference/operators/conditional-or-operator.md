---
title: "|| 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "||_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "|| 演算子 [C#]"
  - "条件 OR 演算子 (||) [C#]"
  - "論理 OR 演算子 [C#]"
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# || 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\(`||`\) 条件OR演算子 `bool` のはオペランドの論理または実行します。  1番目のオペランドが `true`と評価されると、2番目のオペランドは評価されません。  1番目のオペランドが `false`と評価されると、2番目の演算子は、式が `true` か `false`に全体として評価するかどうかを判定します。  
  
## 解説  
  
```  
x || y  
```  
  
 この演算は次の演算に相当します。  
  
```  
x | y  
```  
  
 ただし、`x` が `true`場合、`y` または操作が `y`の値に関係なく `true` であるため、評価されません。  この概念は、「ショートサーキット」評価と呼ばれます。  
  
 条件OR演算子オーバーロードできませんが、通常の論理演算子および [true](../../../csharp/language-reference/keywords/true.md) と [false](../../../csharp/language-reference/keywords/false.md) 演算子のオーバーロードは、特定の制限と、条件論理演算子のオーバーロードと見なされます。  
  
## 使用例  
 次の例では、使用する式は `||` 1番目のオペランドだけが評価されます。  使用する式 `|`両方のオペランドが評価されます。  2番目の例では、ランタイム例外が両方のオペランドが評価されると発生します。  
  
 [!CODE [csRefOperators#52](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#52)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)