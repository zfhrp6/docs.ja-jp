---
title: "Visual Basic の MaskedTextBox コントロールによる正規表現の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 15d8f131aa834321fcf7e8ca633929385c666e6a
ms.lasthandoff: 03/13/2017

---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Visual Basic の MaskedTextBox コントロールによる正規表現を使用する
この例を使用する単純な正規表現に変換する方法、<xref:System.Windows.Forms.MaskedTextBox>コントロール</xref:System.Windows.Forms.MaskedTextBox>。  
  
## <a name="description-of-the-masking-language"></a>マスク言語の説明  
 標準的な<xref:System.Windows.Forms.MaskedTextBox>マスク言語で使用される 1 つに基づいて、`Masked Edit`で制御[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]6.0 し、そのプラットフォームから移行するユーザーにとって理解する必要があります</xref:System.Windows.Forms.MaskedTextBox>。  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>のプロパティ、<xref:System.Windows.Forms.MaskedTextBox>コントロールを使用するどのような入力マスクを指定します</xref:System.Windows.Forms.MaskedTextBox></xref:System.Windows.Forms.MaskedTextBox.Mask%2A>。 マスクは、1 つ以上の次の表からマスク要素から成る文字列である必要があります。  
  
|マスク要素|説明|正規表現の要素|  
|---------------------|-----------------|--------------------------------|  
|0|0 ~ 9 で任意の単一数字です。 入力することができます。|\d|  
|9|数字または空白。 省略可能です。|[ \d]?|  
|#|数字または空白。 省略可能です。 この位置は、マスクの空白のまま、それはスペースとしてレンダリングされます。 プラス記号 (+)、マイナス記号 (-) 記号を許可します。|[ \d+-]?|  
|L|ASCII 文字。 入力することができます。|[- A-za-z]|  
|?|ASCII 文字。 省略可能です。|[- A-za-z] でしょうか。|  
|&|文字です。 入力することができます。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|文字です。 省略可能です。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}] ですか。|  
|A|英数字。 省略可能です。|\W|  
|」を参照してください。|カルチャに応じた小数点のプレース ホルダーです。|使用できません。|  
|、|何千ものカルチャに応じたプレース ホルダーです。|使用できません。|  
|:|カルチャに応じた時刻の区切り記号。|使用できません。|  
|/|カルチャに応じた日付の区切り記号。|使用できません。|  
|$|カルチャに応じた通貨記号。|使用できません。|  
|\<|小文字に変換後に続くすべての文字に変換します。|使用できません。|  
|>|大文字に続くすべての文字に変換します。|使用できません。|  
|&#124;|以前のシフトを元に戻すか、下方向にシフトします。|使用できません。|  
|\|リテラルに変えるマスク文字をエスケープします。 "\\\\"円記号のエスケープ シーケンスです。|\|  
|その他のすべての文字。|リテラルです。 マスク以外のすべての要素は<xref:System.Windows.Forms.MaskedTextBox>。</xref:System.Windows.Forms.MaskedTextBox>自体として表示されます。|その他のすべての文字。|  
  
 小数点 (.)、桁区切り (,)、時間 (:)、日付 (/)、および通貨 ($) 記号は、アプリケーションのカルチャで定義された記号で表示する既定です。 別のカルチャのシンボルを使用して、表示を強制することができます、<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>プロパティ</xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>。  
  
## <a name="regular-expressions-and-masks"></a>正規表現とマスク  
 正規表現とマスクを使用するには、ユーザー入力を検証する、完全に同等ではありません。 正規表現は定型より複雑なパターンを表すことができますが、簡潔にして、カルチャに応じた形式で、マスクは、同じ情報を表すことができます。  
  
 次の表は、それぞれの&4; つの正規表現と等価のマスクを比較します。  
  
|正規表現|マスク|ノート|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`マスク内の文字は、論理上の日付の区切り記号と、アプリケーションの現在のカルチャに適切な日付の区切り記号としてユーザーに表示されます。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|初期文字を大文字小文字の&2; つ続けて&3; 桁の月の省略形が表示される米国形式の日付 (日、月の省略名、および年)。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|アメリカ合衆国の電話番号、市外局番の省略可能です。 ユーザーは省略可能な文字を入力しない場合は、彼女は入力するスペースか最初の 0 で表されるマスク内の位置に直接マウス ポインターを置きます。|  
|`$\d{6}.00`|`$999,999.00`|0 ~ 999999 の範囲の通貨値。 通貨、区切り記号、および&10; 進数の文字は置き換えられます実行時に、対応するカルチャに固有です。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A></xref:System.Windows.Forms.MaskedTextBox.Mask%2A>   
 <xref:System.Windows.Forms.MaskedTextBox></xref:System.Windows.Forms.MaskedTextBox>   
 [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)   
 [MaskedTextBox コントロール](http://msdn.microsoft.com/library/235d6121-027d-481d-8d59-4f6794d15d0c)
