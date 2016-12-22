---
title: "Using Regular Expressions with the MaskedTextBox Control in Visual Basic | Microsoft Docs"
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
  - "strings [Visual Basic], regular expressions"
  - "strings [Visual Basic], masked edit"
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Using Regular Expressions with the MaskedTextBox Control in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

単純な正規表現を変換して <xref:System.Windows.Forms.MaskedTextBox> コントロールで処理する方法は、次のようになります。  
  
## マスク言語について  
 標準の <xref:System.Windows.Forms.MaskedTextBox> のマスク言語は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 の `Masked Edit` コントロールで使用されているものをベースとしているため、そのプラットフォームから移行しているユーザーには見覚えがあるものです。  
  
 <xref:System.Windows.Forms.MaskedTextBox> コントロールの <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> プロパティには、使用する入力マスクを指定します。  マスクは次の表にある 1 つ以上のマスク要素で構成される文字列であることが必要です。  
  
|マスク要素|Description|正規表現要素|  
|-----------|-----------------|------------|  
|0|0 ～ 9 の単一の数字。  入力されていることが必要です。|\\d|  
|9|数字または空白。  入力されていなくてもかまいません。|\[ \\d\]?|  
|\#|数字または空白。  入力されていなくてもかまいません。  この位置がマスク内で空白になっている場合は、空白として表示されます。  正符号 \(\+\) と負符号 \(\-\) が許可されます。|\[ \\d\+\-\]?|  
|L|ASCII 文字。  入力されていることが必要です。|\[a\-zA\-Z\]|  
|?|ASCII 文字。  入力されていなくてもかまいません。|\[a\-zA\-Z\]?|  
|&|文字  入力されていることが必要です。|\[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lm}\\p{Lo}\]|  
|C|文字  入力されていなくてもかまいません。|\[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lm}\\p{Lo}\]?|  
|A|英数字。  入力されていなくてもかまいません。|\\W|  
|.|カルチャに応じた小数点記号。|使用できません。|  
|,|カルチャに応じた桁区切り記号。|使用できません。|  
|:|カルチャに応じた時刻の区切り記号。|使用できません。|  
|\/|カルチャに応じた日付の区切り記号。|使用できません。|  
|$|カルチャに応じた通貨記号。|使用できません。|  
|\<|次に続くすべての文字を小文字に変換します。|使用できません。|  
|\>|次に続くすべての文字を大文字に変換します。|使用できません。|  
|&#124;|直前に行ったシフト アップまたはシフト ダウンを元に戻します。|使用できません。|  
|\\|マスク文字をエスケープし、リテラルに変えます。  "\\\\" は円記号 \(\\\) のエスケープ シーケンスです。|\\|  
|上記以外のすべての文字。|リテラル。  マスク以外の要素は、<xref:System.Windows.Forms.MaskedTextBox> にそのまま表示されます。|上記以外のすべての文字。|  
  
 小数点 \(.\)、桁区切り \(,\)、時刻 \(:\)、日付 \(\/\)、および通貨 \($\) の記号は、既定ではアプリケーションのカルチャで定義された記号で表示されます。  <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> プロパティを使用すると、別のカルチャの記号で表示させることができます。  
  
## 正規表現とマスク  
 正規表現とマスクのどちらを使ってもユーザー入力を検証できますが、この 2 つは完全に同等ではありません。  正規表現を使うとマスクよりも複雑なパターンを表現できますが、マスクを使うと同じ情報をより簡潔に、またカルチャに応じた形式で表現できます。  
  
 正規表現と、それに相当するマスクとの比較を次の表に示します。  
  
|正規表現|マスク|説明|  
|----------|---------|--------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|マスク内の `/` の文字は、論理的な日付の区切り記号であり、ユーザーにはアプリケーションの現在のカルチャに応じた日付の区切り記号が表示されます。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|米国形式の日付 \(日、月の省略形、年\) が表示されます。月の省略形は先頭が大文字、後続の 2 文字が小文字の 3 文字で表示されます。|  
|`(\(\d{3}\)-)?  \d{3}-d{4}`|`(999)-000-0000`|米国形式の電話番号です。エリア コードは省略可能です。  省略可能な文字を入力しない場合は、空白を入力するか、マスク内で最初に 0 で表現されている位置に直接マウス ポインターを置きます。|  
|`$\d{6}.00`|`$999,999.00`|0 ～ 999999 の範囲の通貨の値です。  通貨記号、区切り記号、小数点記号は実行時にそれぞれのカルチャ固有の記号で置き換えられます。|  
  
## 参照  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>   
 <xref:System.Windows.Forms.MaskedTextBox>   
 [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)   
 [MaskedTextBox コントロール](../Topic/MaskedTextBox%20Control%20\(Windows%20Forms\).md)