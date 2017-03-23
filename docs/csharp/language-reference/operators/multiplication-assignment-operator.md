---
title: "*= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "*=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "*= 演算子 [C#]"
  - "二項乗算代入演算子 (*=) [C#]"
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# *= 演算子 (C# リファレンス)
二項乗算代入演算子です。  
  
## 解説  
 次のような `*=` 代入演算子を使用する式があるとします。  
  
```  
x *= y  
```  
  
 上記のコードは、次のコードと同じです。  
  
```  
x = x * y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [\* 演算子](../../../csharp/language-reference/operators/multiplication-operator.md)は、乗算のために数値型に対して組み込まれています。  
  
 `*=` 演算子は直接オーバーロードできませんが、[\* 演算子](../../../csharp/language-reference/operators/multiplication-operator.md)はユーザー定義型でオーバーロードできます。詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)