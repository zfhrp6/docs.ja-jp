---
title: "-- 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "--_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-- 演算子 [C#]"
  - "デクリメント演算子 (--) [C#]"
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# -- 演算子 (C# リファレンス)
デクリメント演算子 \(`--`\) では、オペランドが 1 ずつデクリメントされます。  デクリメント演算子は、オペランドの前または後に指定できます \(`--variable` および `variable--`\)。  最初の形式は、前置デクリメント演算です。  この演算の結果は、"デクリメントが行われた後" のオペランドの値になります。  2 番目の形式は、後置デクリメント演算です。  この演算の結果は、"デクリメントが行われる前" のオペランドの値になります。  
  
## 解説  
 数値型と列挙型には組み込みのデクリメント演算子があります。  
  
 `--` 演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  通常、整数型に対する演算は、列挙に対して適用されます。  
  
## 使用例  
 [!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#8)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)