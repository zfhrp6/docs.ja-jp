---
title: "方法 : Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b92fec7565aad2a881f714f9232eae10bf7633c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>方法 : Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する
Windows フォーム<xref:System.Windows.Forms.DateTimePicker>コントロール柔軟にコントロールにおける日付と時刻の表示の書式設定します。 <xref:System.Windows.Forms.DateTimePicker.Format%2A>プロパティに表示される定義済みの形式から選択することができます、<xref:System.Windows.Forms.DateTimePickerFormat>です。 用途に合わせて適切ながない場合は、形式指定文字を使用して、独自の書式スタイルを作成できます<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>です。  
  
### <a name="to-display-a-custom-format"></a>カスタム書式を表示するには  
  
1.  <xref:System.Windows.Forms.DateTimePicker.Format%2A> プロパティを `DateTimePickerFormat.Custom` に設定します。  
  
2.  設定、<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>書式指定文字列にプロパティです。  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a>テキストを書式設定された値に追加するには  
  
1.  "M"のような形式指定文字またはなどの区切り記号以外の任意の文字を囲む単一引用符を使用して":"です。 たとえば、次の書式指定文字列には、現在の日付形式でが表示されます。"今日: 05:30:31 金曜日 2012 年 3 月 02、"英語 (米国) カルチャ。  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     カルチャ設定に応じて、単一引用符で囲まれていない文字は変更される可能性があります。 たとえば、上記の書式指定文字列には、現在の日付形式でが表示されます。"今日: 05:30:31 金曜日 2012 年 3 月 02、"英語 (米国) カルチャ。 "Hh:mm:ss"であるために区切り記号であるものではありませんので、最初のコロンが単一引用符で囲まれていることに注意してください。 別のカルチャでは、形式がありますとして表示されます"今日: 05.30.31 金曜日 2012 年 3 月 2 日"です。  
  
## <a name="see-also"></a>関連項目  
 [DateTimePicker コントロール](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [方法: Windows フォームの DateTimePicker コントロールを使用して日付を設定および取得する](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
