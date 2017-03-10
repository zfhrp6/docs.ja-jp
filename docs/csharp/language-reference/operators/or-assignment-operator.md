---
title: "|= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "|=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "|= 演算子 (OR 代入) [C#]"
  - "OR 代入演算子 (|=) [C#]"
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# |= 演算子 (C# リファレンス)
OR 代入演算子です。  
  
## 解説  
 次のような `|=` 代入演算子を使用する式があるとします。  
  
```  
x |= y  
```  
  
 上記のコードは、次のコードと同じです。  
  
```  
x = x | y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [&#124; 演算子](../../../csharp/language-reference/operators/or-operator.md)では、整数のオペランドではビットごとの論理 OR 演算、bool オペランドでは論理 OR 演算が実行されます。  
  
 `|=` 演算子は直接オーバーロードできませんが、[&#124; 演算子](../../../csharp/language-reference/operators/or-operator.md)はユーザー定義型でオーバーロードできます。詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#10)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)