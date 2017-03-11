---
title: "Date Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Date"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Date data type"
  - "dates, Visual Basic data types"
  - "times, Date data type"
  - "Date literals"
  - "data values"
  - "times, Visual Basic data types"
  - "dates, Date data type"
  - "data types [Visual Basic], assigning"
  - "literals, Date"
  - "# specifier for Date literals"
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Date Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

IEEE 64 ビット \(8 バイト\) の値として格納され、西暦 0001 年 1 月 1 日から西暦 9999 年 12 月 31 日までの日付と、午前 12:00:00 \(深夜\) から午後 11:59:59.9999999 までの時刻を表します。  各インクリメントはグレゴリオ暦の西暦 1 年 1 月 1 日からの経過時間を 100 ナノ秒で表します。  最大値は、西暦 10000 年 1 月 1 日の 100 ナノ秒前です。  
  
## 解説  
 `Date` データ型は、日付、時刻、またはその両方の値を格納するのに使用します。  
  
 `Date` の既定値は 0001 年 1 月 1 日の 0:00:00 \(深夜\) です。  
  
 <xref:Microsoft.VisualBasic.DateAndTime> クラスから現在の日付および時刻を取得できます。  
  
## 書式の要件  
 `Date` リテラルは、シャープ記号 \(`# #`\) で囲む必要があります。  日付の値は、`#5/31/1993#` のように M\/d\/yyyy の形式で、または `#1993-5-31#` のように yyyy\-MM\-dd の形式で指定する必要があります。  最初に年を指定する場合は、スラッシュを使用できます。  この要件は、ロケールやコンピューターの日付と時刻の設定とは無関係です。  
  
 この制限は、アプリケーションが実行されているロケールによってコードの意味が変わらないようにするために設けられています。  たとえば、`#3/4/1998#` という `Date` リテラルをハード コーディングし、これを 1998 年 3 月 4 日の意味で使用する場合を考えます。  mm\/dd\/yyyy という形式を使用するロケールでは、3\/4\/1998 が意図したとおりにコンパイルされます。  しかし、このアプリケーションを多くの国で展開する場合を考えてみましょう。  dd\/mm\/yyyy という形式を使用するロケールでは、ハード コーディングされたリテラルが 1998 年 4 月 3 日としてコンパイルされます。  yyyy\/mm\/dd という形式を使用するロケールでは、このリテラルは無効な値 \(0003 年 4 月 1998 日\) となり、コンパイラ エラーが発生します。  
  
## 問題回避  
 `Date` リテラルを、使用されるロケールの形式やカスタム形式に変換するには、リテラルを <xref:Microsoft.VisualBasic.Strings.Format%2A> 関数に渡し、定義済みの日付形式またはユーザー定義の日付形式を指定します。  次に例を示します。  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 または、<xref:System.DateTime> 構造体のいずれかのオーバーロードされたコンストラクターを使用して、日付と時刻の値をアセンブルします。  次の例では、1993 年 5 月 31 日午後 12 時 14 分を表す値を作成します。  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)   
```  
  
## 時刻の形式  
 時刻の値は 12 時間制または 24 時間制で指定できます。たとえば、`#1:15:30 PM#` または `#13:15:30#` のようになります。  ただし、分または秒を指定しない場合は、AM または PM を指定する必要があります。  
  
## 日付と時刻の既定値  
 日時のリテラルに日付が含まれない場合は、Visual Basic によって日付の部分の値が 0001 年 1 月 1 日に設定されます。  日時のリテラルに時刻が含まれない場合は、時刻の部分の値が一日の始まり、つまり深夜 0 時 \(0:00:00\) に設定されます。  
  
## 型変換  
 `Date` の値を `String` 型に変換する場合、日付は実行時ロケールで指定された短い日付形式で表示され、時間は実行時ロケールで指定された時刻形式 \(12 時間制または 24 時間制\) で表示されます。  
  
## プログラミングのヒント  
  
-   **相互運用の考慮事項。** オートメーションまたは COM オブジェクトのように、.NET Framework 向けに作成されていないコンポーネントとやり取りする場合、他の環境の日付\/時刻の型は Visual Basic の `Date` 型と互換性がないことに注意してください。  そのようなコンポーネントに日付\/時刻の引数を渡す場合は、新しい Visual Basic のコードで、`Date` 型ではなく `Double` 型として宣言し、<xref:System.DateTime.FromOADate%2A?displayProperty=fullName> および <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> の変換メソッドを使用します。  
  
-   **型宣言文字。** `Date` 型には、リテラルの型文字も識別子の型文字もありません。  ただし、コンパイラでは、シャープ記号 \(`# #`\) で囲まれたリテラルは、日付型 \(`Date`\) として処理されます。  
  
-   **Framework のデータ型** .NET Framework において対応する型は、<xref:System.DateTime?displayProperty=fullName> 構造体です。  
  
## 使用例  
 `Date` データ型の変数または定数は、日付と時刻の両方を格納します。  次に例を示します。  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## 参照  
 <xref:System.DateTime?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [標準の日時書式指定文字列](../Topic/Standard%20Date%20and%20Time%20Format%20Strings.md)   
 [カスタム日時書式指定文字列](../Topic/Custom%20Date%20and%20Time%20Format%20Strings.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)