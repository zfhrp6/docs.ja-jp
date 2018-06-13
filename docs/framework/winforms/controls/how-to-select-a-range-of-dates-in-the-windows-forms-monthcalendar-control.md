---
title: '方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: 8b6d64fcffb02c4496cff3f2821861117b0062fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534061"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する
Windows フォームの重要な特徴<xref:System.Windows.Forms.MonthCalendar>コントロールは、ユーザーが日付の範囲を選択できます。 この機能が、日付選択機能の改良、<xref:System.Windows.Forms.DateTimePicker>コントロールで、ユーザーが 1 つの日付/時刻値を選択できるようにするだけです。 日付の範囲を設定またはのプロパティを使用して、ユーザー設定の選択範囲を取得することができます、<xref:System.Windows.Forms.MonthCalendar>コントロール。 次のコード例では、選択範囲を設定する方法を示します。  
  
### <a name="to-select-a-range-of-dates"></a>日付の範囲を選択するには  
  
1.  作成<xref:System.DateTime>範囲内の最初と最後の日付を表すオブジェクト。  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2.  <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> プロパティを設定します。  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     または  
  
     <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> プロパティと <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> プロパティを設定します。  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>関連項目  
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [方法: Windows フォームの MonthCalendar コントロールの外観を変更する](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [方法: Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [方法: Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
