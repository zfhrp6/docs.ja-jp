---
title: "方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する"
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
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32555097c25a23ca1de6e20308a420d3ec70caf9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="f14c9-102">方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する</span><span class="sxs-lookup"><span data-stu-id="f14c9-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="f14c9-103">Windows フォームの重要な特徴<xref:System.Windows.Forms.MonthCalendar>コントロールは、ユーザーが日付の範囲を選択できます。</span><span class="sxs-lookup"><span data-stu-id="f14c9-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="f14c9-104">この機能が、日付選択機能の改良、<xref:System.Windows.Forms.DateTimePicker>コントロールで、ユーザーが 1 つの日付/時刻値を選択できるようにするだけです。</span><span class="sxs-lookup"><span data-stu-id="f14c9-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="f14c9-105">日付の範囲を設定またはのプロパティを使用して、ユーザー設定の選択範囲を取得することができます、<xref:System.Windows.Forms.MonthCalendar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="f14c9-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="f14c9-106">次のコード例では、選択範囲を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f14c9-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="f14c9-107">日付の範囲を選択するには</span><span class="sxs-lookup"><span data-stu-id="f14c9-107">To select a range of dates</span></span>  
  
1.  <span data-ttu-id="f14c9-108">作成<xref:System.DateTime>範囲内の最初と最後の日付を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f14c9-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
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
  
2.  <span data-ttu-id="f14c9-109"><xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="f14c9-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
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
  
     <span data-ttu-id="f14c9-110">または</span><span class="sxs-lookup"><span data-stu-id="f14c9-110">–or–</span></span>  
  
     <span data-ttu-id="f14c9-111"><xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> プロパティと <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="f14c9-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f14c9-112">参照</span><span class="sxs-lookup"><span data-stu-id="f14c9-112">See Also</span></span>  
 [<span data-ttu-id="f14c9-113">MonthCalendar コントロール</span><span class="sxs-lookup"><span data-stu-id="f14c9-113">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="f14c9-114">方法: Windows フォームの MonthCalendar コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="f14c9-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="f14c9-115">方法: Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する</span><span class="sxs-lookup"><span data-stu-id="f14c9-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="f14c9-116">方法: Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する</span><span class="sxs-lookup"><span data-stu-id="f14c9-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
