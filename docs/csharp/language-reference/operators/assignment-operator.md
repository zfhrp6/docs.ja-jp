---
title: "= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "= 演算子 [C#]"
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# = 演算子 (C# リファレンス)
代入演算子 \(`=`\) では、右辺のオペランドの値が左辺のオペランドで示された格納場所、プロパティ、またはインデクサーに格納され、その値が結果として返されます。  両側のオペランドは、同じ型である必要があります。同じ型でない場合、右辺のオペランドは、左辺のオペランドの型に暗黙に変換できる必要があります。  
  
## 解説  
 代入演算子は、オーバーロードできません。  ただし、暗黙の変換演算子を型に定義すると、それらの型で代入演算子を使用できるようになります。  詳細については、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)