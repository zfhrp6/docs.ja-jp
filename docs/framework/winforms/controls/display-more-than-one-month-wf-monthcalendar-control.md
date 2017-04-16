---
title: "方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する | Microsoft Docs"
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
  - "予定表, 書式指定 (表示を)"
  - "予定表, 複数の月"
  - "例 [Windows フォーム], 予定表コントロール"
  - "MonthCalendar コントロール [Windows フォーム], 書式指定 (表示を)"
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する
Windows フォームの <xref:System.Windows.Forms.MonthCalendar> コントロールでは、最大 12 か月まで一度に表示できます。  既定では 1 つの月だけが表示されますが、表示する月の数と、コントロール内の各月の配置をこのコントロールで指定することもできます。  予定表の大きさを変更すると、コントロールのサイズが変更されます。したがって、新しい大きさに対して十分な領域がフォーム上にあることを確認してください。  
  
### 複数の月を表示するには  
  
-   <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> プロパティに横方向および縦方向に表示する月の数を設定します。  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## 参照  
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [方法 : Windows フォームの MonthCalendar コントロールの外観を変更する](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)