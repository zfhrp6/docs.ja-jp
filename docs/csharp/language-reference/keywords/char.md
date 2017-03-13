---
title: "char (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "char"
  - "char_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "char データ型 [C#]"
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 27
---
# char (C# リファレンス)
`char` のキーワードが Unicode 文字を、.NET Framework を使用する <xref:System.Char?displayProperty=fullName> の構造体のインスタンスを宣言するために使用されます。  `Char` のオブジェクトの値は、16 ビットの数値 \(序数値\) です。  
  
 Unicode 文字で記述された言語のほとんどを世界中で表すために使用されます。  
  
|型|範囲|サイズ|.NET Framework 型|  
|-------|--------|---------|----------------------|  
|`char`|U\+0000 ～ U\+FFFF|Unicode 16 ビット文字|<xref:System.Char?displayProperty=fullName>|  
  
## リテラル  
 `char` 型の定数は、文字リテラル、16 進のエスケープ シーケンス、Unicode 表現として記述できます。  また、整数の文字コードをキャストできます。  次の例では、4 つの `char` 変数を同じ文字 `X` で初期化しています。  
  
 [!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## 変換  
 `char` は、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、または [decimal](../../../csharp/language-reference/keywords/decimal.md) に暗黙的に変換できます。  ただし、他の型から `char` 型への暗黙の型変換はありません。  
  
 <xref:System.Char?displayProperty=fullName> 型は、`char` 値を操作する複数の静的メソッドを備えています。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.Char>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)   
 [文字列](../../../csharp/programming-guide/strings/index.md)