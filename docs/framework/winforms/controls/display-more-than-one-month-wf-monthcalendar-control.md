---
title: '方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する'
ms.date: 03/30/2017
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
ms.openlocfilehash: a71f85af2d51faf37160aba7fa89a8421b4523d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524874"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="5aa52-102">方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する</span><span class="sxs-lookup"><span data-stu-id="5aa52-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="5aa52-103">Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールは、一度に最大 12 か月間を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="5aa52-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="5aa52-104">既定では、コントロールには、1 か月のみが表示されますが、月の数が表示され、コントロール内の配置方法を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="5aa52-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="5aa52-105">カレンダーの次元を変更すると、コントロールのサイズ変更されるため、必ず新しいディメンションのフォームに十分な空き領域があります。</span><span class="sxs-lookup"><span data-stu-id="5aa52-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="5aa52-106">複数の月を表示するには</span><span class="sxs-lookup"><span data-stu-id="5aa52-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="5aa52-107">設定、<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>プロパティを水平方向および垂直方向に表示する月の数。</span><span class="sxs-lookup"><span data-stu-id="5aa52-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5aa52-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="5aa52-108">See Also</span></span>  
 [<span data-ttu-id="5aa52-109">MonthCalendar コントロール</span><span class="sxs-lookup"><span data-stu-id="5aa52-109">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="5aa52-110">方法: Windows フォームの MonthCalendar コントロールで日付の範囲を選択する</span><span class="sxs-lookup"><span data-stu-id="5aa52-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="5aa52-111">方法: Windows フォームの MonthCalendar コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="5aa52-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
