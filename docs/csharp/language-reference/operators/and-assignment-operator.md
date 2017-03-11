---
title: "&amp;= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "&=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "&= 演算子 [C#]"
  - "AND 代入演算子 (&=) [C#]"
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# &amp;= 演算子 (C# リファレンス)
AND 代入演算子です。  
  
## 解説  
 次のような `&=` 代入演算子を使用する式があるとします。  
  
```  
x &= y  
```  
  
 上記のコードは、次のコードと同じです。  
  
```  
x = x & y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [& 演算子](../../../csharp/language-reference/operators/and-operator.md)では、整数のオペランドではビットごとの論理 AND 演算、`bool` オペランドでは論理 AND 演算が実行されます。  
  
 `&=` 演算子は直接オーバーロードできませんが、二項 [& 演算子](../../../csharp/language-reference/operators/and-operator.md)はユーザー定義型でオーバーロードできます。詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#34)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)