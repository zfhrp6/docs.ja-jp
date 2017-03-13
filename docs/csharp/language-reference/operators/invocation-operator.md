---
title: "() 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "()_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "() 演算子 [C#]"
  - "キャスト演算子 [C#]"
  - "型変換 [C#], () 演算子"
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# () 演算子 (C# リファレンス)
かっこは、式の演算順序を指定するだけでなく、次の処理を実行するためにも使用します。  
  
1.  キャストまたは型変換の指定  
  
     [!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  メソッドまたはデリゲートの呼び出し  
  
     [!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## 解説  
 キャストでは、型変換演算子が明示的に呼び出されます。型変換演算子が定義されていない場合、キャストは失敗します。  型変換演算子の定義については、「[explicit](../../../csharp/language-reference/keywords/explicit.md)」および「[implicit](../../../csharp/language-reference/keywords/implicit.md)」を参照してください。  
  
 `()` 演算子はオーバーロードできません。  
  
 詳細については、「[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)」を参照してください。  
  
 キャスト式が原因で構文があいまいになることがあります。  たとえば、`(x)–y` という式は、キャスト式 \(型 x に対する \-y のキャスト\) またはかっこで囲んだ式と組み合わされた加算式 \(値 x \- y を計算する\) のどちらにも解釈できます。  
  
 メソッド呼び出しの詳細については、「[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)