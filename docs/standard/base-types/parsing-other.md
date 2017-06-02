---
title: ".NET Framework におけるその他の文字列の解析 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Char データ型、解析 (文字列を)"
  - "列挙体 [.NET Framework]、解析 (文字列を)"
  - "基本型、解析 (文字列を)"
  - "解析 (文字列を)、その他の文字列"
  - "Boolean データ型、解析 (文字列を)"
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# .NET Framework におけるその他の文字列の解析
数値文字列や <xref:System.DateTime> 文字列のほかに、<xref:System.Char> 型、<xref:System.Boolean> 型、および <xref:System.Enum> 型を表す文字列もデータ型に変換できます。  
  
## Char  
 **Char** データ型に関連付けられている静的な解析メソッドは、単一の文字を含む文字列を Unicode 値に変換するときに便利です。  文字列を Unicode 文字に変換するコード例を次に示します。  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## Boolean  
 **Boolean** データ型には、Boolean 値を表す文字列を実際の **Boolean** 型に変換するために使用できる **Parse** メソッドがあります。  このメソッドは、大文字と小文字を区別せず、"True" または "False" を含む文字列を正しく解析します。**Boolean** 型に関連付けられた **Parse** メソッドは、空白で囲まれた文字列も解析できます。  それ以外の文字列を渡すと、<xref:System.FormatException> がスローされます。  
  
 **Parse** メソッドを使用して文字列を Boolean 値に変換するコード例を次に示します。  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## 列挙型  
 静的な **Parse** メソッドを使用して、列挙型を文字列の値に初期化できます。  このメソッドは、解析する列挙型、解析する文字列、および解析で大文字小文字を区別するかどうかを示すオプションの Boolean フラグを受け入れます。  解析する文字列には、コンマで区切った複数の数値を含めることができます。コンマの前後に 1 つ以上の空白があってもかまいません。  文字列に複数の値が含まれている場合、返されるオブジェクトの値は、指定したすべての値をビットごとの OR 演算で組み合わせた値になります。  
  
 **Parse** メソッドを使用して、文字列形式を列挙値に変換するコード例を次に示します。  <xref:System.DayOfWeek> 列挙体が、文字列から **Thursday** に初期化されます。  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## 参照  
 [文字列の解析](../../../docs/standard/base-types/parsing-strings.md)   
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)   
 [.NET Framework における型変換](../../../docs/standard/base-types/type-conversion.md)