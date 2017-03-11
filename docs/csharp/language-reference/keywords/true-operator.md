---
title: "true 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "true 演算子 [C#]"
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# true 演算子 (C# リファレンス)
オペランドが true であることを示す場合は [bool](../../../csharp/language-reference/keywords/bool.md) 値 `true` を返し、それ以外の場合は `false` を返します。  
  
 C\# 2.0 より前では、`SqlBool` などの型と互換性のあるユーザー定義の null 許容値型を作成するのに `true` 演算子と `false` 演算子が使用されていました。  しかし、現在、null 許容値型の組み込みサポートが追加され、`true` 演算子と `false` 演算子をオーバーロードすることなく、いつでも null 許容値型を使用できるようになりました。  詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。  
  
 null 許容ブール型では、式 `a != b` と `!(a == b)` は必ずしも同じにはなりません。一方または両方の値が null になる可能性があるためです。  式内の null 値を正しく識別するには個別に `true` 演算子と `false` 演算子の両方をオーバーロードする必要があります。  `true` 演算子と `false` 演算子をオーバーロードし、使用する方法を次の例に示します。  
  
 [!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#16)]  
  
 `true` 演算子と `false` 演算子をオーバーロードする型は [if](../../../csharp/language-reference/keywords/if-else.md)、[do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md)、および [for](../../../csharp/language-reference/keywords/for.md) の各ステートメント内の制御式や、[条件式](../../../csharp/language-reference/operators/conditional-operator.md)で使用できます。  
  
 型で `true` 演算子を定義する場合は、[false \(C\# リファレンス\)](../../../csharp/language-reference/keywords/false.md) 演算子も定義する必要があります。  
  
 型は条件論理演算子 \([&amp;&amp; 演算子 \(C\# リファレンス\)](../../../csharp/language-reference/operators/conditional-and-operator.md) および[&#124;&#124; 演算子 \(C\# リファレンス\)](../../../csharp/language-reference/operators/conditional-or-operator.md)\) を直接オーバーロードすることはできません。条件論理演算子を直接オーバーロードする場合と同様の効果を得るには、通常の論理演算子と `true` および `false` の演算子をオーバーロードします。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [false](../../../csharp/language-reference/keywords/false.md)