---
title: "Conversions Between Strings and Other Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "data type conversion, string"
  - "conversions, type"
  - "string conversion"
  - "conversions, data type"
  - "type conversion, string"
  - "regional options"
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conversions Between Strings and Other Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

数値、ブール型 \(`Boolean`\)、または日付\/時刻値は、文字列型 \(`String`\) に変換できます。  文字列の内容が変換先のデータ型での有効な値として解釈される場合には、逆方向 \(文字列値から数値、ブール型 \(`Boolean`\)、日付型 \(`Date`\) にも変換できます。  変換できない場合は、ランタイム エラーが発生します。  
  
 これらすべての代入による変換は、いずれの方向の場合でも縮小変換です。  型変換キーワード \(`CBool`、`CByte`、`CDate`、`CDbl`、`CDec`、`CInt`、`CLng`、`CSByte`、`CShort`、`CSng`、`CStr`、`CUInt`、`CULng`、`CUShort`、および `CType`\) を使用する必要があります。  <xref:Microsoft.VisualBasic.Strings.Format%2A> 関数および <xref:Microsoft.VisualBasic.Conversion.Val%2A> 関数を使用すると、文字列と数値の変換を詳細に制御できます。  
  
 定義されたクラスまたは構造体がある場合、`String` と、クラスまたは構造体の型との間での型変換演算子を定義できます。  詳細については、「[How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)」を参照してください。  
  
## 数値から文字列への変換  
 `Format` 関数を使用すると、数値を書式指定された文字列に変換できます。この文字列には、該当する数字だけでなく、通貨記号 \(`$` など\)、桁区切り記号または*位取り記号* \(`,` など\)、小数点 \(`.` など\) のような書式指定シンボルも含めることができます。  `Format` では、Windows の**コントロール パネル**で指定された **\[地域のオプション\]** の設定に応じて、適切な記号が自動的に使用されます。  
  
 次の例のように、連結演算子 \(`&`\) を使用して数値を文字列に暗黙に変換できます。  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## 文字列から数値への変換  
 文字列内の数字を明示的に数値に変換するには、`Val` 関数を使用できます。  `Val` は、数字、スペース、タブ、改行、またはピリオド以外の文字が検出されるまで文字列を読み取ります。  "&O" や "&H" というシーケンスによって基数法が変わり、スキャンが終了します。  `Val` 関数では、読み取りを停止するまで、すべての該当する文字を数値に変換します。  たとえば、次のステートメントでは値 `141.825` が返されます。  
  
 `Val("   14   1.825 miles")`  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で文字列を数値に変換する場合は、Windows の **\[コントロール パネル\]** の **\[地域のオプション\]** の設定を使用して、桁区切り記号、小数点の記号、および通貨記号が解釈されます。  つまり、ある設定では変換が正常に行われても、別の設定では失敗する場合があります。  たとえば、`"$14.20"` は \[英語 \(U.S.\)\] ロケールでは受け入れることができますが、\[フランス語\] ロケールではできません。  
  
## 参照  
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [.NET Framework ベースの国際対応アプリケーションの概要](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)