---
title: "方法 : Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する | Microsoft Docs"
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
  - "予定表, 表示 (日付を太字で)"
  - "例 [Windows フォーム], 予定表コントロール"
  - "GetDayBold イベント"
  - "MonthCalendar コントロール [Windows フォーム], 日付 (太字で表示される)"
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する
Windows フォームの <xref:System.Windows.Forms.MonthCalendar> コントロールでは、日付を太字で表示できます。これは、単独の日付でも、毎年または毎月繰り返される特定の日付でもかまいません。  祝日や週末など、特別な日を目立つように表示する場合に便利です。  
  
 この機能は、3 つのプロパティによって制御します。  <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> プロパティには、単独の日付が含まれます。  <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> プロパティには、毎年太字で表示する日付が含まれます。  <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> プロパティには、毎月太字で表示する日付が含まれます。  これらの各プロパティには、<xref:System.DateTime> オブジェクトの配列が含まれます。  太字で表示する日付を追加または削除するには、<xref:System.DateTime> オブジェクトを追加または削除します。  
  
### 日付を太字で表示するには  
  
1.  <xref:System.DateTime> オブジェクトを複数個作成します。  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2.  <xref:System.Windows.Forms.MonthCalendar> コントロールの <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>、<xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>、または <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> メソッドを呼び出して、1 つの日付を太字にします。  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     または  
  
     いくつかの日付を一度に太字にするには、<xref:System.DateTime> オブジェクトの配列を作成して、いずれかのプロパティに割り当てます。  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### 日付を通常のフォントで表示するには  
  
1.  <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A> メソッド、<xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A> メソッド、または <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> メソッドを呼び出して、1 つの太字の日付を通常のフォントに戻します。  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     または  
  
     <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A> メソッド、<xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A> メソッド、または <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> メソッドを呼び出して、いずれかのリストから太字の日付をすべて削除します。  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> メソッドを呼び出して、フォントの外観を更新します。  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## 参照  
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [方法 : Windows フォームの MonthCalendar コントロールの外観を変更する](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)   
 [方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)