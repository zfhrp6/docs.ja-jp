---
title: "方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "予定表, 選択 (日付の範囲を)"
  - "日付, 選択 (予定表コントロールから範囲を)"
  - "例 [Windows フォーム], 予定表コントロール"
  - "MonthCalendar コントロール [Windows フォーム], 選択 (日付の範囲を)"
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する
ユーザーが日付の範囲を選択できる機能は、Windows フォームの <xref:System.Windows.Forms.MonthCalendar> コントロールが備える重要な機能です。  この機能は、単一の日付\/時間の値しか選択できない <xref:System.Windows.Forms.DateTimePicker> コントロールの日付選択機能を改善したものです。  <xref:System.Windows.Forms.MonthCalendar> コントロールのプロパティを使用すると、日付の範囲を設定したり、ユーザーが設定した選択範囲を取得できます。  選択範囲を設定する方法を次のコード例に示します。  
  
### 日付の範囲を選択するには  
  
1.  範囲内の最初の日付と最後の日付を表す <xref:System.DateTime> オブジェクトをそれぞれ作成します。  
  
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
  
     <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> プロパティおよび <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> プロパティを設定します。  
  
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
  
## 参照  
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [方法 : Windows フォームの MonthCalendar コントロールの外観を変更する](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)   
 [方法 : Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)   
 [方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)