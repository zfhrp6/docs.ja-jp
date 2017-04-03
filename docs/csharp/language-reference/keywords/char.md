---
title: "char (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bf4c71d6f33d66e5ca917f2cfeb6c882b19b9d22
ms.lasthandoff: 03/13/2017

---
# <a name="char-c-reference"></a>char (C# リファレンス)
`char` キーワードは、Unicode 文字を表すために .NET Framework によって使用される <xref:System.Char?displayProperty=fullName> 構造体のインスタンスを宣言するために使用されます。 `Char` オブジェクトの値は、16 ビット数 (序数) 値です。  
  
 Unicode 文字は、世界各国の文字言語の大半を表すために使用されます。  
  
|型|範囲|サイズ|.NET Framework 型|  
|----------|-----------|----------|-------------------------|  
|`char`|U+0000 ～ U+FFFF|Unicode 16 ビット文字|<xref:System.Char?displayProperty=fullName>|  
  
## <a name="literals"></a>リテラル  
 `char` 型の定数は、文字リテラル、16 進数のエスケープ シーケンス、または Unicode 表現として記述できます。 また、整数の文字コードをキャストすることもできます。 次の例では、4 つの `char` 変数が `X` という同じ文字で初期化されています。  
  
 [!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a>変換  
 `char` は、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、または [decimal](../../../csharp/language-reference/keywords/decimal.md) に暗黙的に変換できます。 ただし、他の型から `char` 型へと暗黙的に変換することはできません。  
  
 <xref:System.Char?displayProperty=fullName> 型では、`char` 値を操作するための静的メソッドがいくつか提供されています。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Char>   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)   
 [文字列](../../../csharp/programming-guide/strings/index.md)
