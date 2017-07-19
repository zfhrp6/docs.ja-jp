---
title: "方法: 文字列を数値に変換する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: be7974018ce3195dc7344192d647fe64fb2ebcc4
ms.openlocfilehash: d406f1731db1e0979be8bba8d10301e57a2281e9
ms.contentlocale: ja-jp
ms.lasthandoff: 05/14/2017

---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>方法: 文字列を数値に変換する (C# プログラミング ガイド)
<xref:System.Convert> クラスのメソッドを使用するか、さまざまな数値型 (int、long、float など) にある `TryParse` メソッドを使用して、[文字列](../../../csharp/language-reference/keywords/string.md)を数値に変換できます。  
  
 文字列では、`TryParse` メソッド (たとえば `int.TryParse("11")`) を呼び出すのがいくらか効率的で簡単です。  <xref:System.IConvertible> を実装している一般的なオブジェクトでは、`Convert` メソッドを使用するのがより便利です。  
  
 文字列に含まれていると思われる数値型 (<xref:System.Int32?displayProperty=fullName> 型など) の `Parse` または `TryParse` メソッドを使用できます。  <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> メソッドは、<xref:System.Int32.Parse%2A> を内部的に使用します。  文字列の形式が無効である場合、`Parse` が例外をスローするのに対し、`TryParse` は [false](../../../csharp/language-reference/keywords/false.md) を返します。  
  
## <a name="example"></a>例  
 文字列の先頭と末尾の空白文字は、`Parse` と `TryParse` メソッドによって無視されますが、その他のすべての文字は、適切な数値型 (int、long、ulong、float、decimal など) を形成する文字である必要があります。  数値を形成する一連の文字内に空白文字があると、エラーになります。  たとえば、"10"、"10.3"、"  10  " を解析するために `decimal.TryParse` を使用することはできますが、"10X"、"1 0" (スペースに注意)、"10 .3" (スペースに注意)、"10e1" (この場合は `float.TryParse` を使用) などからこのメソッドを使用して 10 を解析することはできません。  
  
 以下は、`Parse` および `TryParse` の呼び出しの成功例と失敗例の両方を示しています。  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>例  
 使用できる <xref:System.Convert> クラスのメソッドの例を次の表に示します。  
  
|数値型|メソッド|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 この例では、<xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> メソッドを呼び出して、入力の [string](../../../csharp/language-reference/keywords/string.md) を [int](../../../csharp/language-reference/keywords/int.md) に変換します。 コードは、このメソッドからスローされる最も一般的な 2 種類の例外 (<xref:System.FormatException> と <xref:System.OverflowException>) をキャッチします。 整数の格納場所がオーバーフローすることなく数字をインクリメントできる場合、プログラムは結果に 1 を加算し、出力を印刷します。  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>関連項目  
 [型](../../../csharp/programming-guide/types/index.md)   
 [方法: 文字列が数値を表しているかどうかを確認する](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)   
 [.NET Framework 4 の書式指定ユーティリティ](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
