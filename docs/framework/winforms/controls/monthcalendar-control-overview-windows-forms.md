---
title: "MonthCalendar コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "MonthCalendar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "予定表コントロール, Windows フォーム"
  - "予定表, Windows フォーム コントロール"
  - "MonthCalendar コントロール [Windows フォーム], 設定 (週の最初の曜日を)"
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# MonthCalendar コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.MonthCalendar> コントロールを使用すると、わかりやすいグラフィカル インターフェイスを使用して、日付情報を表示および設定できます。  このコントロールはカレンダー \(曜日の下に当月の日付が配列されたグリッド\) を表示します。日付の選択範囲が強調表示されます。  月表示のキャプションの両側にある矢印ボタンをクリックして、ほかの月を選択できます。  このコントロールでは、類似した <xref:System.Windows.Forms.DateTimePicker> コントロールとは異なり、複数の日付を選択できます。  <xref:System.Windows.Forms.DateTimePicker> コントロールの詳細については、「[DateTimePicker コントロール](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)」を参照してください。  
  
## MonthCalendar コントロールの設定  
 <xref:System.Windows.Forms.MonthCalendar> コントロールの外観には、さまざまな設定方法があります。  既定では、当日の日付が丸で囲まれて表示され、グリッドの下部にも表示されます。  この機能は、<xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> プロパティと <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> プロパティに `false` を設定することで変更できます。  <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> プロパティに `true` を設定して、カレンダーに週番号を表示することもできます。  <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> プロパティの設定によって、複数の月を縦や横に並べて表示することもできます。  既定では週の始まりが日曜日になっていますが、<xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> プロパティで任意の曜日に変更できます。  
  
 特定の日付を太字で表示することもできます。<xref:System.DateTime> オブジェクトを <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> プロパティに追加すると、特定の日付が一度だけ太字で表示されます。<xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> プロパティに追加すると、毎年太字で表示されます。<xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> プロパティに追加すると、毎月太字で表示されます。  詳細については、「[方法 : Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)」を参照してください。  
  
 <xref:System.Windows.Forms.MonthCalendar> コントロールの主要なプロパティは、<xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> プロパティです。このプロパティは、コントロールで選択された日付の範囲を表します。  <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> には、<xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> プロパティに設定された選択可能な日付の数を超える値は指定できません。  ユーザーが選択できる最も古い日付と最も新しい日付は、<xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> プロパティと <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> プロパティで決定します。  
  
## 参照  
 <xref:System.Windows.Forms.MonthCalendar>   
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)