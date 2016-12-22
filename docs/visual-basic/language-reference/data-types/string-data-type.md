---
title: "String Data Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.String"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], character"
  - "strings [Visual Basic], fixed-length"
  - "string keyword [Visual Basic]"
  - "fixed-length strings, string data type"
  - "literals, string"
  - "text [Visual Basic], String data type"
  - "$ identifier type character"
  - "String data type"
  - "fixed-length strings"
  - "string literals"
  - "data types [Visual Basic], assigning"
  - "" String literals"
  - "identifier type characters, $"
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# String Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

0 ～ 65,535 の値を持つ 16 ビット \(2 バイト\) の符号なしコード ポイントのシーケンスを格納します。  各*コード ポイント* \(文字コード\) は、単一の Unicode 文字を表します。  文字列型には、0 ～約 20 億個 \(2^31\) までの Unicode 文字を格納できます。  
  
## 解説  
 `String` データ型を使用すると、`Char()` の配列管理のオーバーヘッド、つまり `Char` 要素の配列を管理するオーバーヘッドをかけることなく、複数の文字を格納できます。  
  
 `String` の既定値は `Nothing` \(null 参照\) です。  これは空の文字列 \(値 `""`\) とは異なるので注意してください。  
  
## Unicode 文字  
 Unicode の最初の 128 個のコード ポイント \(0 ～ 127\) は、標準の英語版キーボードの文字と記号に  対応します。  これら最初の 128 個のコード ポイントは、ASCII 文字セットで定義された文字と同じです。  次の 128 個のコード ポイント \(128 ～ 255\) は、ラテン語系のアルファベット、アクセント記号、通貨記号、分数などの特殊文字を表します。  Unicode は、その他のコード ポイント \(256\-65535\) を使用してさまざまな記号を表します。  たとえば、各言語の文字、発音符、数学記号、技術記号などの記号を表します。  
  
 `String` 変数に含まれる個々の文字に対して <xref:System.Char.IsDigit%2A> や <xref:System.Char.IsPunctuation%2A> などのメソッドを使用すると、Unicode の分類を判別できます。  
  
## 書式の要件  
 `String` のリテラルは、二重引用符 \(`" "`\) で囲む必要があります。  文字列の 1 文字として二重引用符を含める場合は、二重引用符を 2 つ続けて \(`""`\) 記述する必要があります。  次に例を示します。  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 連続した二重引用符のうち、文字列に含まれる二重引用符は、`String` のリテラルを開始および終了する二重引用符と関係ないことに注意してください。  
  
## 文字列操作の概要  
 文字列を `String` 変数に代入すると、その文字列は*変更不可*になります。つまり、文字列の長さや内容を変更できなくなります。  何らかの方法で文字列を変更すると、Visual Basic は新しい文字列を作成し、変更前の文字列を破棄します。  これにより、`String` 変数は新しい文字列をポイントするようになります。  
  
 `String` 変数の内容は、さまざまな文字列関数を使って操作できます。  次に <xref:Microsoft.VisualBasic.Strings.Left%2A> 関数の例を示します。  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 別のコンポーネントで作成された文字列には、先頭または末尾に空白が埋め込まれていることがあります。  このような文字列を受け取った場合に、<xref:Microsoft.VisualBasic.Strings.Trim%2A>、<xref:Microsoft.VisualBasic.Strings.LTrim%2A>、および <xref:Microsoft.VisualBasic.Strings.RTrim%2A> の各関数を使用して空白を削除できます。  
  
 文字列操作の詳細については、「[Strings](../../../visual-basic/programming-guide/language-features/strings/index.md)」を参照してください。  
  
## プログラミングのヒント  
  
-   **負の数。** `String` に格納される文字には符号がないため、負の値を表現できないことに注意してください。  どのような場合でも、`String` を使って数値を格納しないでください。  
  
-   **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 向けに作成されていないコンポーネントを使用する場合、他の環境では文字列の各文字のデータ幅が異なる \(8 ビット\) ことに注意してください。  Visual Basic コードを作成する際、8 ビット文字の文字列引数をこのようなコンポーネントに渡す場合は、引数を `String` ではなく、`Byte()` として、つまり `Byte` 要素の配列として宣言してください。  
  
-   **型宣言文字。** 任意の識別子に識別子の型文字 `$` を付けると、`String` データ型に変換されます。  `String` にはリテラルの型文字はありません。  ただし、コンパイラでは、二重引用符 \(`" "`\) で囲まれたリテラルは文字列型 \(`String`\) として処理されます。  
  
-   **Framework のデータ型。** .NET Framework において対応する型は、<xref:System.String?displayProperty=fullName> クラスです。  
  
## 参照  
 <xref:System.String?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)