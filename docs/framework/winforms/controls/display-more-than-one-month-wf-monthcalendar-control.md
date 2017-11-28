---
title: "方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する"
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
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cf236f93fa3352e536c71000f6bb110abf02fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する
Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールは、一度に最大 12 か月間を表示することができます。 既定では、コントロールには、1 か月のみが表示されますが、月の数が表示され、コントロール内の配置方法を指定することができます。 カレンダーの次元を変更すると、コントロールのサイズ変更されるため、必ず新しいディメンションのフォームに十分な空き領域があります。  
  
### <a name="to-display-multiple-months"></a>複数の月を表示するには  
  
-   設定、<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>プロパティを水平方向および垂直方向に表示する月の数。  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>関連項目  
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [方法: Windows フォームの MonthCalendar コントロールで日付の範囲を選択する](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [方法: Windows フォームの MonthCalendar コントロールの外観を変更する](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
