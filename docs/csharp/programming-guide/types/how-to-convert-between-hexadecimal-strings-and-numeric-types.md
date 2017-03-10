---
title: "方法: 16 進文字列と数値型の間で変換する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "変換 [C#], 16 進文字列"
  - "16 進文字列 [C#]"
  - "16 進文字列 [C#], 変換 (数値型に)"
  - "文字列 [C#], 変換 (16 進文字列を)"
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# 方法: 16 進文字列と数値型の間で変換する (C# プログラミング ガイド)
以下の例では、次のタスクを実行する方法を説明します。  
  
-   [string](../../../csharp/language-reference/keywords/string.md) の各文字の 16 進値を取得する。  
  
-   16 進文字列の各値に対応する [char](../../../csharp/language-reference/keywords/char.md) を取得する。  
  
-   16 進 `string` を [int](../../../csharp/language-reference/keywords/int.md) に変換する。  
  
-   16 進 `string` を [float](../../../csharp/language-reference/keywords/float.md) に変換する。  
  
-   [バイト](../../../csharp/language-reference/keywords/byte.md)配列を 16 進 `string` に変換する。  
  
## 使用例  
 この例では、`string` の各文字の 16 進値を出力しています。  まず `string` を解析し、文字配列に変換します。  次に、各文字に対して <xref:System.Convert.ToInt32%28System.Char%29> を呼び出し、その数値を取得します。  最後に、その数を 16 進表現で `string` に書式設定します。  
  
 [!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-between-h_1.cs)]  
  
## 使用例  
 この例は、16 進値の `string` を解析し、各 16 進値に対応する文字を出力しています。  まず、[Split\(Char\<xref:System.String.Split%28System.Char%5B%5D%29> メソッドを呼び出して、各 16 進値を配列内の個別の `string` として取得します。  次に、<xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> を呼び出して、16 進値を [int](../../../csharp/language-reference/keywords/int.md) で表される 10 進値に変換します。  ここでは、その文字コードに対応する文字を取得するための異なる 2 つの方法を示しています。  その 1 つは、<xref:System.Char.ConvertFromUtf32%28System.Int32%29> を使用する方法です。このメソッドは、整数引数に対応する文字を `string` として返します。  もう 1 つは、`int` を明示的に [char](../../../csharp/language-reference/keywords/char.md) にキャストする方法です。  
  
 [!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-between-h_2.cs)]  
  
## 使用例  
 この例は、<xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> メソッドを呼び出すことにより 16 進 `string` を整数に変換する方法を示しています。  
  
 [!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-between-h_3.cs)]  
  
## 使用例  
 <xref:System.BitConverter?displayProperty=fullName> クラスと <xref:System.Int32.Parse%2A?displayProperty=fullName> メソッドを使用して 16 進 `string` を [float](../../../csharp/language-reference/keywords/float.md) に変換する方法を、次の例に示します。  
  
 [!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-between-h_4.cs)]  
  
## 使用例  
 <xref:System.BitConverter?displayProperty=fullName> クラスを使用して[バイト](../../../csharp/language-reference/keywords/byte.md)配列を 16 進文字列に変換する方法を、次の例に示します。  
  
 [!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-between-h_5.cs)]  
  
## 参照  
 [標準の数値書式指定文字列](../Topic/Standard%20Numeric%20Format%20Strings.md)   
 [型](../../../csharp/programming-guide/types/index.md)   
 [方法 : 文字列が数値を表しているかどうかを確認する](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)