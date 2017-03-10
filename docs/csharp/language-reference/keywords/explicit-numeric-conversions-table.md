---
title: "明示的な数値変換の一覧表 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "変換 [C#], 明示的な数値"
  - "明示的な数値変換 [C#]"
  - "数値変換 [C#], explicit"
  - "数値データ型 [C#]"
  - "型変換 [C#], 明示的な数値"
  - "型 [C#], 明示的な数値変換"
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 明示的な数値変換の一覧表 (C# リファレンス)
暗黙の型変換が行われない場合に、明示的な数値の変換を行います。キャスト式を使用して任意の数値型を他の数値型に変換します。  これらの変換を次に示します。  
  
 変換の詳細については、[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md) のトピックを参照してください。  
  
|変換前|目的|  
|---------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`、`ushort`、`uint`、`ulong`、または `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` または `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`、 `byte`、 `ushort`、 `uint`、 `ulong`、または  `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`、 `byte`、 `short`、または  `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `uint`、 `ulong`、または ``  `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`、`byte`、 `short`、 `ushort`、 `int`、または  `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `int`、 `uint`、 `ulong`、または  `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`、 `byte`、 `short`, `ushort`、 `int`、 `uint`、 `long`、または  `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`、`byte`、または  `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `int`、 `uint`、 `long`、 `ulong`、 `char`、または ``  `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `int`、 `uint`、 `long`、 `ulong`、 `char`、 `float`、 `` または ``  `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `int`、 `uint`、 `long`、 `ulong`、 `char`、 `float`、または  `double`|  
  
## 解説  
  
-   明示的な数値変換によって、有効桁数が桁落ちしたり、例外がスローされる場合があります。  
  
-   `decimal` 値を整数型に変換すると、値は一番近い整数値に丸められます。  結果の整数値が変換先の型の範囲を超えた場合は、<xref:System.OverflowException> がスローされます。  
  
-   `double` 値または `float` 値を整数型に変換すると、値が切り捨てられます。  整数値が、変換後の値の範囲を超えた場合は、オーバーフロー チェック コンテキストに従います。  checked コンテキストでは、`OverflowException` がスローされます。これに対して、unchecked コンテキストでは、変換後の型の未指定値に変換されます。  
  
-   `double` から `float` への変換では、`double` 値は最も近い `float` 値に丸められます。  `double` 値が、変換後の型の範囲外であるため格納できない場合は、0 または無限大になります。  
  
-   `float` または `double` から `decimal` への変換では、変換前の値が `decimal` 表記に変換され、必要に応じて小数第 28 位までの近似値に丸められます。  変換元の値に応じて、次のいずれかが生じる場合があります。  
  
    -   変換元の値が小さすぎて `decimal` で表すことができない場合、結果は 0 になります。  
  
    -   変換元の値が非数 \(NaN\)、無限大、または大きすぎて `decimal` で表すことができない場合は、`OverflowException` がスローされます。  
  
-   `decimal` から `float` または `double` への変換では、`decimal` 値は最も近い `double` 値または `float` 値に丸められます。  
  
 明示的な変換の詳細については、『C\# 言語仕様』の「明示的な変換」を参照してください。  仕様にアクセスする方法の詳細については、「[C\# 言語仕様](../../../csharp/language-reference/language-specification.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [\(\) 演算子](../../../csharp/language-reference/operators/invocation-operator.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)