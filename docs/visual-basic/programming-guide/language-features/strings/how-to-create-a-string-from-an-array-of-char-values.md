---
title: "How to: Create a String from An Array of Char Values (Visual Basic) | Microsoft Docs"
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
  - "examples [Visual Basic], arrays"
  - "examples [Visual Basic], Char data type"
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a String from An Array of Char Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

個別の文字から文字列 "abcd" を作成する例を次に示します。  
  
## 使用例  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## コードのコンパイル  
 このメソッドには、特別な要件はありません。  
  
 単一文字 `c` が二重引用符に囲まれた単一文字の後に続く構文 `"a"c` は、文字リテラルを作成するために使用されます。  
  
## 信頼性の高いプログラミング  
 文字列の中に `Chr(0)` に相当する null 文字があると、文字列を使用するときに予想外の結果になります。  文字列に null 文字が含まれる場合、状況によっては null 文字の後の文字が表示されないことがあります。  
  
## 参照  
 <xref:System.String>   
 [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)