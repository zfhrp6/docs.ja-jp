---
title: "方法: 16 進文字列と数値型の間で変換する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: 19
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5852e79f551ce88e0ca54de159abbc222d769234
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>方法: 16 進文字列と数値型の間で変換する (C# プログラミング ガイド)
以下の例では、次のタスクを実行する方法について説明します。  
  
-   [string](../../../csharp/language-reference/keywords/string.md) の各文字の 16 進値を取得する。  
  
-   16 進文字列の各値に対応する [char](../../../csharp/language-reference/keywords/char.md) を取得する。  
  
-   16 進 `string` を [int](../../../csharp/language-reference/keywords/int.md) に変換する。  
  
-   16 進 `string` を [float](../../../csharp/language-reference/keywords/float.md) に変換する。  
  
-   [バイト](../../../csharp/language-reference/keywords/byte.md)配列を 16 進 `string` に変換する。  
  
## <a name="example"></a>例  
 この例では、`string` の各文字の 16 進値を出力しています。 まず `string` を解析し、文字配列に変換します。 次に、各文字で <xref:System.Convert.ToInt32%28System.Char%29> を呼び出し、その数値を取得します。 最後に、その数を 16 進表現で `string` に書式設定します。  
  
 [!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a>例  
 この例は、16 進値の `string` を解析し、各 16 進値に対応する文字を出力しています。 まず、[Split(Char\[\])](xref:System.String.Split(System.Char[])) メソッドを呼び出して、各 16 進値を配列内の個別の `string` として取得します。 次に、<xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> を呼び出して、16 進値を [int](../../../csharp/language-reference/keywords/int.md) で表される 10 進値に変換します。 ここでは、その文字コードに対応する文字を取得するための 2 つの方法を示しています。 1 つは、<xref:System.Char.ConvertFromUtf32%28System.Int32%29> を使用する方法です。これは、整数引数に対応する文字を `string` として返します。 もう 1 つは、`int` を明示的に [char](../../../csharp/language-reference/keywords/char.md) にキャストする方法です。  
  
 [!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a>例  
 次の例は、<xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> メソッドを呼び出すことにより 16 進 `string` を整数に変換する方法を示しています。  
  
 [!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a>例  
 次の例は、<xref:System.BitConverter?displayProperty=fullName> クラスと <xref:System.Int32.Parse%2A?displayProperty=fullName> メソッドを使用して、16 進 `string` を [float](../../../csharp/language-reference/keywords/float.md) に変換する方法を示しています。  
  
 [!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a>例  
 次の例は、<xref:System.BitConverter?displayProperty=fullName> クラスを使用して[バイト](../../../csharp/language-reference/keywords/byte.md)配列を 16 進文字列に変換する方法を示しています。  
  
 [!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a>関連項目  
 [標準の数値書式指定文字列](http://msdn.microsoft.com/library/580e57eb-ac47-4ffd-bccd-3a1637c2f467)   
 [型](../../../csharp/programming-guide/types/index.md)   
 [方法: 文字列が数値を表しているかどうかを確認する](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)

