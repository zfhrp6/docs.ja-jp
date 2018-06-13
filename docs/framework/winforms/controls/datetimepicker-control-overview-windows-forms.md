---
title: DateTimePicker コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: cf44cdff7da06a27921ce5881199a3a88b1096f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528355"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.DateTimePicker>コントロールによりユーザーは日付または時刻の一覧から 1 つの項目を選択します。 2 つの部分に表示される日付の表示に使用する場合: テキスト、および一覧の横の下向きの矢印をクリックしたときに表示されるグリッドで表される日付のドロップダウン リスト。 次のように、グリッド、<xref:System.Windows.Forms.MonthCalendar>コントロールで、複数の日付を選択するために使用できます。 詳細については、<xref:System.Windows.Forms.MonthCalendar>を制御しを参照してください[MonthCalendar コントロールの概要](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md)です。  
  
## <a name="key-properties"></a>キー プロパティ  
 希望する場合、<xref:System.Windows.Forms.DateTimePicker>ピッキングまたは日付ではなく時間を編集するためのコントロールとして表示するには設定、<xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A>プロパティを`true`と<xref:System.Windows.Forms.DateTimePicker.Format%2A>プロパティを<xref:System.Windows.Forms.DateTimePickerFormat.Time>です。 詳細については、次を参照してください。[する方法: DateTimePicker コントロールに表示時間](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md)です。  
  
 ときに、<xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A>プロパティに設定されている`true`コントロールで選択した日付の横にあるチェック ボックスが表示されます。 チェック ボックスをオンにすると、選択した日付と時刻の値を更新できます。 チェック ボックスが空の場合は、値が使用できなくなったが表示されます。  
  
 コントロールの<xref:System.Windows.Forms.DateTimePicker.MaxDate%2A>と<xref:System.Windows.Forms.DateTimePicker.MinDate%2A>プロパティは、日付と時刻の範囲を決定します。 <xref:System.Windows.Forms.DateTimePicker.Value%2A>プロパティには、現在の日付と時刻に設定されているコントロールが含まれています。 詳細については、「[する方法: セットと Windows フォームの DateTimePicker コントロールを使用して日付を返す](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)です。 によって設定される、4 つの形式で値を表示することができます、<xref:System.Windows.Forms.DateTimePicker.Format%2A>プロパティ: <xref:System.Windows.Forms.DateTimePickerFormat.Long>、 <xref:System.Windows.Forms.DateTimePickerFormat.Short>、 <xref:System.Windows.Forms.DateTimePickerFormat.Time>、または<xref:System.Windows.Forms.DateTimePickerFormat.Custom>です。 設定する必要があります、カスタム書式を選択している場合、<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>プロパティを適切な文字列にします。 詳細については、「[する方法: Windows フォームの DateTimePicker コントロールを備えたカスタム形式で日付を表示](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)  
 [方法: Windows フォームの DateTimePicker コントロールを使用して日付を設定および取得する](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
