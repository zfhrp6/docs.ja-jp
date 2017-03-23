---
title: "変換の概要 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data type conversion, keywords
- reference, type conversions
- conversions, Visual Basic
- type conversion, keywords
ms.assetid: ae2c79a7-2d62-4fbe-8585-14360d11f987
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 05ea9ba57cc2d6f5f3d05d6e623527958b9dc1eb
ms.lasthandoff: 03/13/2017

---
# <a name="conversion-summary-visual-basic"></a>変換の概要 (Visual Basic)
以下の表は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 言語のキーワードとランタイム ライブラリ メンバーを目的および使用方法別に分類したものです。  
  
|アクション|言語要素|  
|------------|----------------------|  
|ANSI 値から文字列への変換|<xref:Microsoft.VisualBasic.Strings.Chr%2A>,<xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A>|  
|文字列をすべて小文字または大文字に変換|<xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Strings.LCase%2A>,<xref:Microsoft.VisualBasic.Strings.UCase%2A></xref:Microsoft.VisualBasic.Strings.UCase%2A></xref:Microsoft.VisualBasic.Strings.LCase%2A></xref:Microsoft.VisualBasic.Strings.Format%2A>|  
|日付をシリアル値に変換|<xref:Microsoft.VisualBasic.DateAndTime.DateSerial%2A>,<xref:Microsoft.VisualBasic.DateAndTime.DateValue%2A></xref:Microsoft.VisualBasic.DateAndTime.DateValue%2A></xref:Microsoft.VisualBasic.DateAndTime.DateSerial%2A>|  
|10 進数を&16; 進数または&8; 進数に変換|<xref:Microsoft.VisualBasic.Conversion.Hex%2A>,<xref:Microsoft.VisualBasic.Conversion.Oct%2A></xref:Microsoft.VisualBasic.Conversion.Oct%2A></xref:Microsoft.VisualBasic.Conversion.Hex%2A>|  
|数値を文字列に変換|<xref:Microsoft.VisualBasic.Strings.Format%2A>,<xref:Microsoft.VisualBasic.Conversion.Str%2A></xref:Microsoft.VisualBasic.Conversion.Str%2A></xref:Microsoft.VisualBasic.Strings.Format%2A>|  
|データ型間の変換|[CBool](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CByte](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CDate](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CDbl](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CDec](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CInt](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CLng](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CSng](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CShort](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CStr](../../../visual-basic/language-reference/functions/type-conversion-functions.md), [CType](../../../visual-basic/language-reference/functions/ctype-function.md), <xref:Microsoft.VisualBasic.Conversion.Fix%2A>, <xref:Microsoft.VisualBasic.Conversion.Int%2A></xref:Microsoft.VisualBasic.Conversion.Int%2A></xref:Microsoft.VisualBasic.Conversion.Fix%2A>|  
|日付を日、月、曜日、または年に変換|<xref:Microsoft.VisualBasic.DateAndTime.Day%2A>, <xref:Microsoft.VisualBasic.DateAndTime.Month%2A>, <xref:Microsoft.VisualBasic.DateAndTime.Weekday%2A>, <xref:Microsoft.VisualBasic.DateAndTime.Year%2A></xref:Microsoft.VisualBasic.DateAndTime.Year%2A></xref:Microsoft.VisualBasic.DateAndTime.Weekday%2A></xref:Microsoft.VisualBasic.DateAndTime.Month%2A></xref:Microsoft.VisualBasic.DateAndTime.Day%2A>|  
|時刻を時、分、または秒に変換|<xref:Microsoft.VisualBasic.DateAndTime.Hour%2A>, <xref:Microsoft.VisualBasic.DateAndTime.Minute%2A>, <xref:Microsoft.VisualBasic.DateAndTime.Second%2A></xref:Microsoft.VisualBasic.DateAndTime.Second%2A></xref:Microsoft.VisualBasic.DateAndTime.Minute%2A></xref:Microsoft.VisualBasic.DateAndTime.Hour%2A>|  
|文字列を ASCII 値に変換|<xref:Microsoft.VisualBasic.Strings.Asc%2A>,<xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A>|  
|文字列を数値に変換|<xref:Microsoft.VisualBasic.Conversion.Val%2A></xref:Microsoft.VisualBasic.Conversion.Val%2A>|  
|時刻をシリアル値に変換|<xref:Microsoft.VisualBasic.DateAndTime.TimeSerial%2A>,<xref:Microsoft.VisualBasic.DateAndTime.TimeValue%2A></xref:Microsoft.VisualBasic.DateAndTime.TimeValue%2A></xref:Microsoft.VisualBasic.DateAndTime.TimeSerial%2A>|  
  
## <a name="see-also"></a>関連項目  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Visual Basic ランタイム ライブラリのメンバー](../../../visual-basic/language-reference/runtime-library-members.md)
