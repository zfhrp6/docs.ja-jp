---
title: "&amp;&amp; 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "&&_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "&& 演算子 [C#]"
  - "論理 AND 演算子 [C#]"
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# &amp;&amp; 演算子 (C# リファレンス)
条件 AND 演算子 \(`&&`\) では `bool` オペランドの論理 AND が実行されますが、必要な場合のみ、2 番目のオペランドが評価されます。  
  
## 解説  
  
```  
x && y  
```  
  
 この演算は次の演算に相当します。  
  
```  
x & y  
```  
  
 ただし`x` が `false` 場合`y` は `y` の値と演算結果が `false` であるためは評価されません。  これは、"ショートサーキット" 評価と呼ばれます。  
  
 条件 AND 演算子はオーバーロードできませんが、通常の論理演算子および [true](../../../csharp/language-reference/keywords/true.md) 演算子と [false](../../../csharp/language-reference/keywords/false.md) 演算子のオーバーロードは、条件論理演算子の制約付きのオーバーロードとも見なされます。  
  
## 使用例  
 次の例では`if` の 2 番目のステートメントの条件式はオペランドが `false` を返すため1 番目のオペランドだけが評価されます。  
  
 [!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)