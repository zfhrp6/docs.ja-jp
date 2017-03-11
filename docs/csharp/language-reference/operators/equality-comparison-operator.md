---
title: "== 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "==_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "== 演算子 [C#]"
  - "等値演算子 [C#]"
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# == 演算子 (C# リファレンス)
組み込みの値型の場合、等値演算子 \(`==`\) ではオペランドの値が等しい場合に true が返され、それ以外の場合は `false` が返されます。  [string](../../../csharp/language-reference/keywords/string.md) 以外の参照型の場合、`==` では 2 つのオペランドが同じオブジェクトを参照する場合に `true` が返されます。  `string` 型の場合は、`==` は文字列の値を比較します。  
  
## 解説  
 `==` 演算子はユーザー定義の値型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  ユーザー定義の参照型でオーバーロードはできますが、既定では、組み込み参照型とユーザー定義参照型のいずれに対しても `==` は前述のとおりに機能します。  `==` をオーバーロードする場合は、[\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) もオーバーロードする必要があります。  通常、整数型に対する演算は、列挙に対して適用されます。  
  
## 使用例  
 [!code-cs[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#36)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)