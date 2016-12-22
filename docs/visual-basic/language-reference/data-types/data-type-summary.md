---
title: "Data Type Summary (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean data type, supported types in Visual Basic"
  - "storage, order of storage"
  - "data types [Visual Basic], Visual Basic"
  - "Single data type, supported types in Visual Basic"
  - "notation, scientific"
  - "memory requirements, data types"
  - "user-defined data types, Visual Basic"
  - "Date data type, Visual Basic"
  - "Visual Basic, data types"
  - "storage, allocation"
  - "Integer data type, Visual Basic data types"
  - "storage, space"
  - "Variant data types, supported types in Visual Basic"
  - "Char data type, Visual Basic data types"
  - "intrinsic data types"
  - "memory consumption, data types"
  - "single-precision numbers"
  - "data types [Visual Basic], order of storage"
  - "Long data type, supported types in Visual Basic"
  - "String data type, Visual Basic data types"
  - "storage order, data types"
  - "StructLayoutAttribute class, Visual Basic data type storage"
  - "scientific notation"
  - "Double data type, Visual Basic data types"
  - "Byte data type, Visual Basic data types"
  - "Object data type, supported types in Visual Basic"
  - "data types [Visual Basic], storage allocation"
  - "double-precision numbers"
  - "data types [Visual Basic], summary"
  - "dates [Visual Basic], data types"
  - "strings [Visual Basic], data types"
  - "memory consumption"
  - "storage order, controlling in Visual Basic"
  - "data types [Visual Basic], memory requirements"
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Data Type Summary (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic のデータ型の一覧を次の表に示します。それぞれのデータ型について、サポートされている共通言語ランタイムの型、ストレージ割り当ての公称サイズ、および値の範囲を示しています。  
  
|Visual Basic のデータ型|共通言語ランタイムの型構造|ストレージ割り当ての公称サイズ|値の範囲|  
|------------------------|-------------------|---------------------|----------|  
|[Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|実装するプラットフォームに依存|`True` または `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 バイト|0 ～ 255 \(符号なし\)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) \(文字型、1 文字\)|<xref:System.Char>|2 バイト|0 ～ 65535 \(符号なし\)|  
|[日付](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 バイト|0001 年 1 月 1 日 0:00:00 \(午前 0 時\) ～ 9999 年 12 月 31 日 11:59:59 PM|  
|[Decimal \(10 進数型\)](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 バイト|0 ～ \+\/\-79,228,162,514,264,337,593,543,950,335 \(\+\/\-7.9...E\+28\) <sup>†</sup> \(小数点なし\)、0 ～ \+\/\-7.9228162514264337593543950335 \(小数点以下 28 桁\)<br /><br /> 0 以外の最小数は \+\/\-0.0000000000000000000000000001 \(\+\/\-1E\-28\) <sup>†</sup>|  
|[Double](../../../visual-basic/language-reference/data-types/double-data-type.md) \(倍精度浮動小数点数型\)|<xref:System.Double>|8 バイト|\-1.79769313486231570E\+308 ～ \-4.94065645841246544E\-324 <sup>†</sup> \(負の値\)<br /><br /> 4.94065645841246544E\-324 ～ 1.79769313486231570E\+308 <sup>†</sup> \(正の値\)|  
|[Integer \(整数型\)](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 バイト|\-2,147,483,648 ～ 2,147,483,647 \(符号付き\)|  
|[Long](../../../visual-basic/language-reference/data-types/long-data-type.md) \(長整数型\)|<xref:System.Int64>|8 バイト|\-9,223,372,036,854,775,808 ～ 9,223,372,036,854,775,807 \(9.2...E\+18 <sup>†</sup>\) \(符号付き\)|  
|[Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> \(クラス\)|32 ビット プラットフォームでは 4 バイト<br /><br /> 64 ビット プラットフォームでは 8 バイト|オブジェクト型 \(`Object`\) の変数には任意の型を格納できます。|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 バイト|\-128 ～ 127 \(符号付き\)|  
|[Short](../../../visual-basic/language-reference/data-types/short-data-type.md) \(短整数型\)|<xref:System.Int16>|2 バイト|\-32,768 ～ 32,767 \(符号付き\)|  
|[Single](../../../visual-basic/language-reference/data-types/single-data-type.md) \(単精度浮動小数点数\)|<xref:System.Single>|4 バイト|\-3.4028235E\+38 ～ \-1.401298E\-45 <sup>†</sup> \(負の値\)<br /><br /> 1.401298E\-45 ～ 3.4028235E\+38 <sup>†</sup> \(正の値\)|  
|[String](../../../visual-basic/language-reference/data-types/string-data-type.md) \(可変長\)|<xref:System.String> \(クラス\)|実装するプラットフォームに依存|0 個 ～ 約 20 億個の Unicode 文字|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 バイト|0 ～ 4,294,967,295 \(符号なし\)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 バイト|0 ～ 18,446,744,073,709,551,615 \(1.8...E\+19 <sup>†</sup>\) \(符号なし\)|  
|[ユーザー定義型](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) \(構造体\)|\(<xref:System.ValueType> から継承\)|実装するプラットフォームに依存|構造体の各メンバーの範囲はデータ型によって決まり、他のメンバーの範囲とは関係しません。|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 バイト|0 ～ 65,535 \(符号なし\)|  
  
 <sup>†</sup> *指数表記*では、"E" は 10 のべき乗を表します。  つまり、3.56E\+2 は 3.56 x 10<sup>2</sup> または 356 を表し、3.56E\-2 は 3.56 \/ 10<sup>2</sup> または 0.0356 を表します。  
  
> [!NOTE]
>  テキストを含む文字列の場合は、<xref:Microsoft.VisualBasic.Strings.StrConv%2A> 関数を使用してテキスト形式を変換できます。  
  
 データ型を指定するだけでなく申告のステートメント、型文字を使用してなるプログラミング要素のデータ型を強制できます。  「[Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)」を参照してください。  
  
## メモリの使用量  
 基本データ型を宣言する場合、そのメモリの使用量がストレージ割り当ての公称サイズと同じであると仮定するのは安全ではありません。  これは、次の考慮事項によるものです。  
  
-   **ストレージの割り当て。**共通言語ランタイムは、アプリケーションが実行されるプラットフォームの現在の特性に基づいてストレージを割り当てます。  メモリがほぼ満杯である場合、宣言された要素を可能な限り 1 つにまとめます。  その他の場合、メモリ アドレスを自然なハードウェアの境界まで配置し、パフォーマンスを最適化します。  
  
-   **プラットフォームの幅。**ストレージ割り当ては、64 ビット プラットフォームの場合と 32 ビット プラットフォームの場合とで異なります。  
  
### 複合データ型  
 構造体や配列などの複合データ型の各メンバーに対しても、同じことが当てはまります。  単に型のメンバーのストレージ割り当ての公称サイズを合計するだけでは不十分です。  さらに、次のような考慮事項もあります。  
  
-   **オーバーヘッド。**一部の複合型には、別のメモリ要件もあります。  たとえば配列は、配列それ自体に対してと、各次元に対して、それぞれ別個のメモリを使用します。  32 ビット プラットフォームでは、現在このオーバーヘッドは 12 バイトに加えて各次元について 8 バイトです。  64 ビットでは、この要件が 2 倍になります。  
  
-   **ストレージのレイアウト。**さらに、メモリ内に格納される順序が宣言の順序と同じであると仮定するのも安全ではありません。  2 バイトまたは 4 バイトの境界など、バイトの配置を仮定することもできません。  クラスまたは構造体を定義するときに、そのメンバーのストレージのレイアウトを制御する必要がある場合、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性をそのクラスまたは構造体に割り当てます。  
  
### オブジェクトのオーバーヘッド  
 基本データ型または複合データ型を参照するオブジェクト型 \(`Object`\) は、データ型に含まれるデータのほかに、さらに 4 バイトを使用します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)