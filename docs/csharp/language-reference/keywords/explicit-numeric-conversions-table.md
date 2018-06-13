---
title: 明示的な数値変換の一覧表 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 7363df3e4b2449924222745de409fd68349b93de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218385"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>明示的な数値変換の一覧表 (C# リファレンス)
明示的な数値変換は、暗黙的変換がないときに、キャスト式を利用し、任意の数値型を他の数値型に変換するために利用します。 次の表はこの変換についてまとめたものです。  
  
 変換の詳細については、「[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)」を参照してください。  
  
|From|終了|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`、`ushort`、`uint`、`ulong`、または `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` または `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`、`byte`、`ushort`、`uint`、`ulong`、または `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`、`byte`、`short`、または `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong`、または `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、または `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`ulong`、または `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、または `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`、 `byte`、または `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、または `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、または `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、または `double`|  
  
## <a name="remarks"></a>コメント  
  
-   明示的な数値変換では、精度が失われたり、例外がスローされることがあります。  
  
-   `decimal` 値を整数型に変換するとき、この値は 0 方向に最も近い整数値に丸められます。 結果的に生成される整数値が変換先の型の範囲外になった場合、<xref:System.OverflowException> がスローされます。  
  
-   `double` または `float` 値から整数型に変換するとき、値に切り捨てが行われます。 結果的に生成される整数値が変換先の値の範囲外になる場合、結果はオーバーフロー チェック コンテキストによって変わります。 チェック済みコンテキストの場合、`OverflowException` がスローされます。未チェック コンテキストの場合、結果は変換先の型の未指定値になります。  
  
-   `double` を `float` に変換すると、`double` 値は最も近い `float` 値に丸められます。 `double` 値が小さすぎるか、大きすぎて変換先の型に合わない場合、結果は 0 か無限になります。  
  
-   `float` または `double` を `decimal` に変換するとき、変換元の値は `decimal` 表現に変換され、必要であれば、28 番目の小数位の後に最も近い数字に丸められます。 変換元の値によっては、結果は次のいずれかになります。  
  
    -   変換元の値が小さすぎて `decimal` として表現できない場合、結果は 0 になります。  
  
    -   変換元の値が NaN (Not a Number/数字ではない) か、無限か、大きすぎて `decimal` として表現できない場合、`OverflowException` がスローされます。  
  
-   `decimal` を `float` または `double` に変換すると、`decimal` 値は最も近い `double` または `float` 値に丸められます。  
  
 明示的な変換の詳細については、「C# 言語仕様」の「明示的」を参照してください。 仕様にアクセスする方法については、「[C# のドラフト言語仕様](../../../csharp/language-reference/language-specification/index.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [() 演算子](../../../csharp/language-reference/operators/invocation-operator.md)  
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
