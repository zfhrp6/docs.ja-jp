---
title: "Char Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Char"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literal type characters, C"
  - "Char data type"
  - "C literal type character"
  - "data types [Visual Basic], assigning"
  - "Char data type, character literals"
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Char Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

0 ～ 65,535 の値を持つ符号なしの 16 ビット \(2 バイト\) コード ポイントを保持します。  各*コード ポイント* \(文字コード\) は、単一の Unicode 文字を表します。  
  
## 解説  
 単独の文字を扱う場合に `String` のオーバーヘッドを避けるには `Char` データ型を使用します。  複数の文字を扱う場合に、`Char` 要素の配列である `Char()` を使用することもできます。  
  
 `Char` の既定値は、コード ポイント 0 を持つ文字です。  
  
## Unicode 文字  
 Unicode の最初の 128 個のコード ポイント \(0 ～ 127\) は、標準の英語版キーボードの文字と記号に  対応します。  これら最初の 128 個のコード ポイントは、ASCII 文字セットで定義された文字と同じです。  次の 128 個のコード ポイント \(128 ～ 255\) は、ラテン語系のアルファベット、アクセント記号、通貨記号、分数などの特殊文字を表します。  Unicode はその他のコード ポイント \(256\-65535\) を使用して、各言語の文字、発音符、数学記号、技術記号などのさまざまな記号を表します。  
  
 <xref:System.Char.IsDigit%2A> や <xref:System.Char.IsPunctuation%2A> などのメソッドを `Char` 型の変数で使用すると、Unicode の分類を判別できます。  
  
## 型変換  
 Visual Basic では、`Char` 型と数値型の直接変換は行われません。  `Char` の値を、対応するコード ポイントを表す `Integer` に変換するには、<xref:Microsoft.VisualBasic.Strings.Asc%2A> 関数または <xref:Microsoft.VisualBasic.Strings.AscW%2A> 関数を使用します。  `Integer` の値を、このコード ポイントを持つ `Char` に変換するには、<xref:Microsoft.VisualBasic.Strings.Chr%2A> 関数または <xref:Microsoft.VisualBasic.Strings.ChrW%2A> 関数を使用します。  
  
 型チェックのスイッチ \([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)\) がオンの場合、これが `Char` データ型であることを識別するために、リテラル型の文字を 1 文字の文字列に追加します。  次に例を示します。  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## プログラミングのヒント  
  
-   **負の数。** `Char` は符号なしのデータ型で、負の値を表すことはできません。  数値を格納するのに `Char` は使用しません。  
  
-   **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 向けに作成されていないコンポーネントを使用する場合、他の環境では文字型のデータ幅が異なる \(8 ビット\) ことに注意してください。  そのようなコンポーネントに 8 ビットの引数を渡す場合は、新しい Visual Basic のコードで、`Char` 型ではなく `Byte` 型として宣言します。  
  
-   **拡大変換。** `Char` データ型は、`String` に拡大されます。  つまり、`Char` は <xref:System.OverflowException?displayProperty=fullName> エラーにならずに `String` に変換できます。  
  
-   **型宣言文字。** 1 文字のリテラル文字列に、リテラルの型文字 `C` を追加すると、`Char` データ型に変換されます。  `Char` には識別子の型文字はありません。  
  
-   **Framework のデータ型。** .NET Framework において対応する型は、<xref:System.Char?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.Char?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)