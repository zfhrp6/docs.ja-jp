---
title: MonthCalendar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: 7ed917afe2640fe2ffef4904a3795c5f0e84ded9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537409"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールがユーザーを表示し、日付情報を設定するための直感的なグラフィカル インターフェイスを表示します。 カレンダーを表示します。 は月、日、曜日、強調表示されている日付の選択範囲の下にある列に配置の番号付きの日を含むグリッドです。 月のキャプションのどちらかの側にある矢印ボタンをクリックして、別の月を選択できます。 異なり、類似<xref:System.Windows.Forms.DateTimePicker>コントロール、このコントロールに 1 つ以上の日付を選択できます。 詳細については、<xref:System.Windows.Forms.DateTimePicker>を制御しを参照してください[DateTimePicker コントロール](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)です。  
  
## <a name="configuring-the-monthcalendar-control"></a>MonthCalendar コントロールの構成  
 <xref:System.Windows.Forms.MonthCalendar>コントロールの外観は柔軟な構成です。 既定では、今日の日付が丸で囲まれて表示され、グリッドの下部にも示されます。 設定してこの機能を変更することができます、<xref:System.Windows.Forms.MonthCalendar.ShowToday%2A>と<xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A>プロパティ`false`です。 設定して、予定表に週番号を追加することも、<xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A>プロパティを`true`です。 設定して、<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>プロパティ、複数の水平方向および垂直方向に表示する月を持つことができます。 既定は、日曜日が、その週の最初の日として表示されますを使用して任意の日を指定することができます、<xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>プロパティです。  
  
 設定することもに表示される特定の日付、または月単位、1 回限りのベースで太字を追加して<xref:System.DateTime>オブジェクトを<xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>、 <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>、および<xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>プロパティです。 詳細については、次を参照してください。[する方法: Windows フォームの MonthCalendar コントロールでの太字の特定の日数を表示](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)です。  
  
 キー プロパティ、<xref:System.Windows.Forms.MonthCalendar>コントロールが<xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>コントロールで選択されている日付の範囲です。 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>値が選択できる設定日数の最大数を超えることはできません、<xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>プロパティです。 ユーザーが選択できる最初と最後の日付がによって決定されます、<xref:System.Windows.Forms.MonthCalendar.MaxDate%2A>と<xref:System.Windows.Forms.MonthCalendar.MinDate%2A>プロパティです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MonthCalendar>  
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
