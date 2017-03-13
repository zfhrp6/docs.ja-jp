---
title: "as (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "as_CSharpKeyword"
  - "as"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "as キーワード [C#]"
  - "型変換 [C#], as キーワード"
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# as (C# リファレンス)
互換性のある参照型または [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)間の変換の特定の種類の実行に `as` の演算子を使用できます。  次に例を示します。  
  
 [!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## 解説  
 `as` 演算子はキャスト操作とよく似ています。  ただし、変換可能でない場合、`as` は、例外は発生せず、`null` を返します。  次に例を示します。  
  
```  
expression as type  
```  
  
 コードは次の式と同等ですが、`expression` の変数は、1 回だけ評価されます。  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 `as` の演算子は参照の変換、null 許容変換とボックス化変換だけ実行します。  `as` の演算子は他の変換を使用して、キャスト式を使用して実行する必要があるユーザー定義の変換など実行できません。  
  
## 使用例  
 [!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [?: 演算子](../../../csharp/language-reference/operators/conditional-operator.md)   
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)