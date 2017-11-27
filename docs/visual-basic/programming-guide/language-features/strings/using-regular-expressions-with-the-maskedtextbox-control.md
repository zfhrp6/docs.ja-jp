---
title: "Visual Basic の MaskedTextBox コントロールによる正規表現を使用する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2638ed804593dd52481bd3865e1c67c5fdb2dcf9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Visual Basic の MaskedTextBox コントロールによる正規表現を使用する
この例で使用する簡単な正規表現に変換する方法、<xref:System.Windows.Forms.MaskedTextBox>コントロール。  
  
## <a name="description-of-the-masking-language"></a>マスク言語の説明  
 標準<xref:System.Windows.Forms.MaskedTextBox>マスク言語に基づきますで使用される、`Masked Edit`で制御[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]6.0 し、そのプラットフォームから移行するユーザーにとって理解する必要があります。  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>のプロパティ、<xref:System.Windows.Forms.MaskedTextBox>コントロールを使用するどのような入力マスクを指定します。 マスクは、1 つまたは複数の次の表からマスク要素で構成される文字列にする必要があります。  
  
|マスク要素|説明|正規表現要素|  
|---------------------|-----------------|--------------------------------|  
|0|すべて 1 桁の数字 0 ~ 9 の範囲です。 入力してください。|\d|  
|9|数字またはスペース。 省略可能です。|[\d] しますか。|  
|#|数字またはスペース。 省略可能です。 この位置は、マスクで空白のままには、領域としてレンダリングされます。 プラス記号 (+) マイナス記号 (-) 記号が許可されているとします。|[\d+-] しますか。|  
|L|ASCII 文字。 入力してください。|[a, A-z]|  
|?|ASCII 文字。 省略可能です。|[a, A-z] しますか。|  
|&|文字です。 入力してください。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|文字です。 省略可能です。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]。|  
|A|英数字です。 省略可能です。|\W|  
|」を参照してください。|カルチャに応じた小数点のプレース ホルダーです。|使用できません。|  
|、|何千ものカルチャに応じたプレース ホルダーです。|使用できません。|  
|:|カルチャに応じた時刻の区切り記号。|使用できません。|  
|/|カルチャに応じた日付の区切り記号。|使用できません。|  
|$|カルチャに応じた通貨記号。|使用できません。|  
|\<|小文字に変換後に続くすべての文字に変換します。|使用できません。|  
|>|大文字に続くすべての文字に変換します。|使用できません。|  
|&#124;|以前 shift キーを元に戻すか、下方向にシフトします。|使用できません。|  
|\|リテラルに、マスク文字をエスケープします。 "\\\\"円記号のエスケープ シーケンスです。|\|  
|その他のすべての文字。|リテラルです。 マスク以外のすべての要素は自体が表示されます内<xref:System.Windows.Forms.MaskedTextBox>です。|その他のすべての文字。|  
  
 小数点 (.)、桁区切り (,)、(:)、(/)、日付と時刻 ($) の通貨記号、アプリケーションのカルチャによって定義されたこれらのシンボルを表示するのには、既定です。 使用して別のカルチャのシンボルを表示することを強制することができます、<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>プロパティです。  
  
## <a name="regular-expressions-and-masks"></a>正規表現とマスク  
 正規表現とマスクを使用するには、ユーザー入力を検証する、完全に同等ではありません。 正規表現は、定型より複雑なパターンを表すことができますより簡潔にあり、カルチャに適切な形式で、マスクは、同じ情報を表すことができます。  
  
 次の表は、それぞれの 4 つの正規表現と同等のマスクを比較します。  
  
|正規表現|マスク|メモ|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`マスク内の文字は論理日付の区切り記号、およびアプリケーションの現在のカルチャに適切な日付の区切り記号としてユーザーに表示されます。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|初期文字を大文字小文字の 2 つ続けて 3 桁の月の省略形が表示されている米国形式の日付 (1 日、月の省略形、および year) です。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|米国の電話番号、市外局番の省略可能です。 ユーザーが省略可能な文字を入力を含まれていない場合、彼女はスペースを入力したり最初の 0 で表されるマスク内の位置に直接マウス ポインターを置きます。|  
|`$\d{6}.00`|`$999,999.00`|0 ~ 999999 の範囲の通貨値です。 通貨、区切り記号、および 10 進数の文字は、対応するカルチャ固有の実行時に置き換えられます。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)  
 [MaskedTextBox コントロール](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
