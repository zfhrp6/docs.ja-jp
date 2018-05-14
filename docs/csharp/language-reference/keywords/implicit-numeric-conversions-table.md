---
title: 暗黙的な数値変換の一覧表 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 2d417a2020656f300de0517526742679388f262e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>暗黙的な数値変換の一覧表 (C# リファレンス)
定義済みの暗黙的な数値変換を次の表に示します。 暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。  
  
|From|終了|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`、`int`、`long`、`float`、`double`、または `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`、`long`、`float`、`double`、または `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`、`float`、`double`、または `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`、`ulong`、`float`、`double`、または `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`、 `double`、または `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、または `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`、 `double`、または `decimal`|  
  
## <a name="remarks"></a>コメント  
  
-   `int`、`uint`、`long`、または `ulong` から `float` への変換と `long` から `ulong` または `double` への変換では、有効桁数が失われる場合があります (絶対値ではありません)。  
  
-   `char` 型への暗黙的な変換はありません。  
  
-   浮動小数点型と `decimal` 型の間に、暗黙的な変換はありません。  
  
-   `int` 型の定数式は、定数式の値が変換後の型の範囲内にある場合、`sbyte`、`byte`、`short`、`ushort`、`uint`、または `ulong` に変換できます。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
