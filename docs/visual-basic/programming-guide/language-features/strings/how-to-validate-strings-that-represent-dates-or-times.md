---
title: "How to: Validate Strings That Represent Dates or Times (Visual Basic) | Microsoft Docs"
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
  - "strings [Visual Basic], validating"
  - "String data type, validation"
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Validate Strings That Represent Dates or Times (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

次のコード例は、文字列が有効な日付または時刻を表しているかどうかを示す `Boolean` 値を設定します。  
  
## 使用例  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## コードのコンパイル  
 `("01/01/03")` および `"9:30 PM"` は、実際に検証する日付と時刻に置き換えてください。  この文字列は、別のハードコーディングされた文字列、`String` 変数、または文字列を返す `InputBox` などのメソッドで置き換えることができます。  
  
## 信頼性の高いプログラミング  
 このメソッドを使うと、`String` を `DateTime` 変数に変換する前に文字列を検証できます。  日付または時刻を最初にチェックすることにより、実行時に例外が生成されることを回避できます。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>   
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>   
 [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)