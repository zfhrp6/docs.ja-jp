---
title: "^= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "^=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "^= 演算子 [C#]"
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# ^= 演算子 (C# リファレンス)
排他的 OR 代入演算子です。  
  
## 解説  
 次のような形式の式があるとします。  
  
```  
x ^= y  
```  
  
 この式は、次のように評価されます。  
  
```  
x = x ^ y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)では、整数のオペランドではビットごとの排他的 OR 演算、[bool](../../../csharp/language-reference/keywords/bool.md) オペランドでは排他的論理和が実行されます。  
  
 ^\= 演算子は直接オーバーロードできませんが、ユーザー定義型では [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)をオーバーロードできます \(「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照\)。  
  
## 使用例  
 [!code-cs[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)