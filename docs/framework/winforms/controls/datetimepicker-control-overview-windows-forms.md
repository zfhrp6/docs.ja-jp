---
title: "DateTimePicker コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DateTimePicker"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "日時指定コントロール"
  - "DateTimePicker コントロール [Windows フォーム], 概要"
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# DateTimePicker コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.DateTimePicker> コントロールは、日付や時間のリストから 1 つの項目を選択するためのコントロールです。  このコントロールで日付を表す場合、テキスト表示された日付のドロップダウン リストと、その隣の下向きの矢印をクリックしたときに表示されるグリッドの 2 つの部分で構成されます。  グリッドは、複数の日付を選択できる <xref:System.Windows.Forms.MonthCalendar> コントロールに似ています。  <xref:System.Windows.Forms.MonthCalendar> コントロールの詳細については、「[MonthCalendar コントロールの概要](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md)」を参照してください。  
  
## 主要なプロパティ  
 日付の代わりに時間の指定と編集を行うコントロールとして <xref:System.Windows.Forms.DateTimePicker> を表示する場合は、<xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> プロパティに `true` を設定し、<xref:System.Windows.Forms.DateTimePicker.Format%2A> プロパティに <xref:System.Windows.Forms.DateTimePickerFormat> を設定します。  詳細については、「[方法 : DateTimePicker コントロールを使用して時間を表示する](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> プロパティに `true` を設定すると、コントロールの選択した日付の横に、チェック ボックスが表示されます。  チェック ボックスをオンにすると、選択した日時の値を更新できます。  チェック ボックスをオフにすると、値は利用できません。  
  
 日付と時間の範囲を決定するのは、コントロールの <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> プロパティと <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> プロパティです。  <xref:System.Windows.Forms.DateTimePicker.Value%2A> プロパティには、コントロールに設定されている現在の日付と時間が格納されています。  詳細については、「[方法 : Windows フォームの DateTimePicker コントロールを使用して日付を設定および取得する](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)」を参照してください。  値は <xref:System.Windows.Forms.DateTimePickerFormat>、<xref:System.Windows.Forms.DateTimePickerFormat>、<xref:System.Windows.Forms.DateTimePickerFormat>、または <xref:System.Windows.Forms.DateTimePickerFormat> の 4 つの形式で表示できます。これは <xref:System.Windows.Forms.DateTimePicker.Format%2A> プロパティで設定します。  Custom 形式を選択した場合は、<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> プロパティに適切な文字列を設定する必要があります。  詳細については、「[方法 : Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)」を参照してください。  
  
## 参照  
 [方法 : Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)   
 [方法 : Windows フォームの DateTimePicker コントロールを使用して日付を設定および取得する](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)