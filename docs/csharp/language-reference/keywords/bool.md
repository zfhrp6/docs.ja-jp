---
title: "bool (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "bool_CSharpKeyword"
  - "bool"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "bool キーワード [C#]"
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# bool (C# リファレンス)
`bool` キーワードは、<xref:System.Boolean?displayProperty=fullName> のエイリアスです。  ブール値 \([true](../../../csharp/language-reference/keywords/true.md) および [false](../../../csharp/language-reference/keywords/false.md)\) を格納する変数を宣言するときに使用します。  
  
> [!NOTE]
>  `null` の値も受け取ることができるブール変数が必要な場合は、`bool?` を使用します。  詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。  
  
## リテラル  
 `bool` 変数にはブール値を代入できます。  `bool` として評価される式を `bool` 変数に代入することもできます。  
  
 [!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 `bool` 変数の既定値は `false` です。  `bool?` 変数の既定値は `null` です。  
  
## 変換  
 C\+\+ では、`bool` 型の値を `int` 型の値に変換できます。つまり、`false` は 0 と等価であり、`true` は 0 以外の値と等価です。  C\# では、`bool` 型とその他の型は変換できません。  たとえば、C\# では次の `if` ステートメントは無効です。  
  
 [!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 `int` 型の変数をテストするには、次のように、明示的に特定の値 \(たとえば 0\) と比較する必要があります。  
  
 [!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## 使用例  
 ここでは、キーボードから文字が入力されると、入力文字がアルファベットかどうかをチェックするプログラムの例を示します。  アルファベットの場合は、大文字か小文字かをチェックします。  これらのチェックは、<xref:System.Char.IsLetter%2A> および <xref:System.Char.IsLower%2A> を使用して実行され、この両方が `bool` 型を返します。  
  
 [!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)