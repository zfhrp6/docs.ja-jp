---
title: "value (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "value_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "value キーワード [C#]"
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# value (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コンテキスト キーワード `value` は、set アクセサーの通常のプロパティ宣言で使用します。  これは、メソッドの入力パラメーターに似ています。  `value` という語は、クライアント コードでプロパティに割り当てる値を表します。  次の例の `MyDerivedClass` には、`Name` というプロパティがあります。このプロパティは `value` パラメーターを使用して、バッキング フィールド `name` に新しい文字列を割り当てます。  クライアント コードから見ると、演算は簡単な代入演算として記述されます。  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 `value` の使用に関する詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)