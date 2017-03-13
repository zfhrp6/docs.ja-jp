---
title: "Character Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "data types [Visual Basic], character"
  - "String data type, character data types"
  - "character data types [Visual Basic]"
  - "Char data type, character data types"
  - "data types [Visual Basic], choosing"
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# Character Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、出力する文字や表示する文字を処理する*文字データ型*が用意されています。  char 型 \(`Char`\) は 1 文字、文字列型 \(`String`\) は不特定数の文字を格納します。どちらの型も Unicode 文字を処理します。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] データ型の side\-by\-side の比較を示す表については、「[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)」を参照してください。  
  
## char 型 \(Char\)  
 char データ型 \(`Char`\) は、2 バイト \(16 ビット\) の Unicode 文字の 1 文字です。  常に 1 文字しか格納しない変数の場合は、`Char` として宣言します。  次に例を示します。  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 `Char` または `String` 変数で指定可能な値は、Unicode 文字セット内の*コード ポイント*、または文字コードです。  Unicode 文字には、基本 ASCII 文字セット、その他各種のアルファベット文字、アクセント、通貨記号、分数、発音記号、数学および科学技術記号が含まれます。  
  
> [!NOTE]
>  Unicode 文字セットでは、コード ポイント D800 ～ DFFF \(10 進数表現で 55296 ～ 55551\) を*サロゲート ペア*用に予約します。サロゲート ペアでは、単一のコード ポイントを表すのに 2 つの 16 ビット値が必要です。  `Char` 変数では、サロゲート ペアを保持することはできません。また、`String` では、このようなペアを保持するためには 2 桁を使用します。  
  
 詳細については、「[Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)」を参照してください。  
  
## 文字列型 \(String\)  
 文字列型 \(`String`\) は、0 個以上の 2 バイト \(16 ビット\) の Unicode 文字列です。  変数に格納する文字数が不定の場合は、変数を `String` 型で宣言します。  次に例を示します。  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 詳細については、「[String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)」を参照してください。  
  
## 参照  
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)