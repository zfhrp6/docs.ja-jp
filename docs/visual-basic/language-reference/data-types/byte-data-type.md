---
title: "Byte Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Byte"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Byte data type"
  - "data types [Visual Basic], assigning"
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Byte Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

0 から 255 までの符号なし 8 ビット \(1 バイト\) の整数です。  
  
## 解説  
 `Byte` データ型はバイナリ データの格納に使用します。  
  
 `Byte` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **負の数。** `Byte` 型は符号を持たないので、負の数を表現できません。  バイト型 \(`Byte`\) を評価する式で単項マイナス演算子 \(`-`\) を使用すると、Visual Basic では、最初に式が `Short` 型に変換されます。  
  
-   **形式の変換。**Visual Basic がファイルを読み書きするとき、または DLL、メソッド、プロパティを呼び出すとき、データ形式が自動的に変換されます。  バイト型 \(`Byte`\) の変数および配列に格納されるバイナリ データは、形式変換中に保存されます。  バイナリ データに文字列型 \(`String`\) の変数を使用しないでください。これは、ANSI 形式と Unicode 形式の変換時にデータの内容が破損する場合があるためです。  
  
-   **拡大変換。** `Byte` データ型は、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、または `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `Byte` を変換できることを意味します。  
  
-   **型宣言文字。** `Byte` 型には、リテラルの型文字も識別子の型文字もありません。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.Byte?displayProperty=fullName> 構造体です。  
  
## 使用例  
 次の例では、`b` は `Byte` 型変数です。  このステートメントは、変数の範囲と、その範囲にビット シフト演算子を適用する例を示しています。  
  
 [!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/byte-data-type_1.vb)]  
  
## 参照  
 <xref:System.Byte?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)