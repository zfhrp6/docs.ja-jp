---
title: "implicit (C# リファレンス) | Microsoft Docs"
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
  - "implicit"
  - "implicit_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "implicit キーワード [C#]"
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# implicit (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`implicit` キーワードを使用して、暗黙のユーザー定義型変換演算子を宣言します。  変換を実行してもデータ損失が発生する心配がない場合に、ユーザー定義型からその他の型、またはその他の型からユーザー型への暗黙の型変換を有効にするために使用します。  
  
## 使用例  
 [!CODE [csrefKeywordsConversion#5](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsConversion#5)]  
  
 不要なキャストを省けるため、暗黙の型変換を行う場合はソース コードが読みやすくなります。  ただし、暗黙の型変換では、一方の型からもう一方の型へ明示的にキャストする必要がないため、予期しない結果が発生しないように注意する必要があります。  暗黙の演算子は、通常、プログラマが変換を認識していなくても安全に使用できるように、変換中に例外をスローしたり情報を失ったりしないことが必要です。  このような条件を満たせない変換演算子には、`explicit` キーワードを使用する必要があります。  詳細については、「[変換演算子の使用 \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)   
 [方法 : 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)