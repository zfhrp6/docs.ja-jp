---
title: 数値結果テーブルの書式設定 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: cc215971d63a0ee61eb25ac45834a81fbbc50b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="formatting-numeric-results-table-c-reference"></a>数値結果テーブルの書式設定 (C# リファレンス)
数値結果の書式を指定するには、<xref:System.String.Format%2A?displayProperty=nameWithType> メソッドを使用するか、`String.Format` を呼び出す <xref:System.Console.Write%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> メソッドを使用するか、[文字列補間](../tokens/interpolated.md)を使用します。 書式を指定するには、書式指定文字列を使用します。 サポートされる標準の書式指定文字列を次の表に示します。 書式指定文字列は `Axx` という形式になります。この `A` は書式指定子、`xx` は精度指定子です。 書式指定子は、数値に適用する書式の種類を制御し、精度指定子は、書式付き出力の有効桁数または小数点以下の桁数を制御します。 精度指定子の値は 0 から 99 の範囲です。  
  
 標準およびカスタム書式指定文字列の詳細については、「[Formatting Types](../../../standard/base-types/formatting-types.md)」(型の書式設定) を参照してください。
  
|書式指定子|説明|使用例|出力|  
|----------------------|-----------------|--------------|------------|  
|C または c|通貨|Console.Write("{0:C}", 2.5);<br /><br /> Console.Write("{0:C}", -2.5);|$2.50<br /><br /> ($2.50)|  
|D または d|Decimal (10 進数型)|Console.Write("{0:D5}", 25);|00025|  
|E または e|指数|Console.Write("{0:E}", 250000);|2.500000E+005|  
|F または f|固定小数点|Console.Write("{0:F2}", 25);<br /><br /> Console.Write("{0:F0}", 25);|25.00<br /><br /> 25|  
|G または g|全般|Console.Write("{0:G}", 2.5);|2.5|  
|N または n|数値|Console.Write("{0:N}", 2500000);|2,500,000.00|  
|X または x|16 進数|Console.Write("{0:X}", 250);<br /><br /> Console.Write("{0:X}", 0xffff);|FA<br /><br /> FFFF|  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [標準の数値書式指定文字列](../../../standard/base-types/standard-numeric-format-strings.md)  
 [型のリファレンス表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [string](../../../csharp/language-reference/keywords/string.md)
