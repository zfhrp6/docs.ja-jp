---
title: "暗黙的な数値変換の一覧表 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "変換 [C#], 暗黙の数値"
  - "暗黙の数値変換 [C#]"
  - "数値変換 [C#], implicit"
  - "型 [C#], 暗黙の数値変換"
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# 暗黙的な数値変換の一覧表 (C# リファレンス)
組み込まれた暗黙の数値変換を次に示します。  暗黙の変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。  
  
|変換前|目的|  
|---------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`、`int`、`long`、`float`、`double`、または `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`、`long`、`float`、`double`、または `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`、`float`、`double`、または `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`、`ulong`、`float`、`double`、または `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`、`double`、または `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`、`int`、 `uint`、 `long`、`ulong`、 `float`、 `double`、または `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`、 `double`、または `decimal`|  
  
## 解説  
  
-   精度が大きさではない可能性があります失わからの変換で`int`、 `uint`、 `long`、または`ulong`に`float`から`long`または`ulong`に`double`。  
  
-   `char` 型への暗黙の型変換はありません。  
  
-   浮動小数点型と `decimal` 型の間には、暗黙の型変換はありません。  
  
-   `int` 型の定数式は、定数式の値が変換後の型の範囲内である場合、`sbyte`、`byte`、`short`、`ushort`、`uint`、または `ulong` に変換できます。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)