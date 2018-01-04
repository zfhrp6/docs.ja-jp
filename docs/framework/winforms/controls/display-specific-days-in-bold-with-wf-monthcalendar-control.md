---
title: "方法 : Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する"
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
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 141d943c4f4dfc3976e66e13e7c0975aba3f1687
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="3dfb4-102">方法 : Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する</span><span class="sxs-lookup"><span data-stu-id="3dfb4-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="3dfb4-103">Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールは、単数形の日付として、または繰り返しごとに、太字での日数を表示できます。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="3dfb4-104">休日や週末などの特別な日を目立たせるこれを行う場合があります。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="3dfb4-105">次の 3 つのプロパティは、この機能を制御します。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-105">Three properties control this feature.</span></span> <span data-ttu-id="3dfb4-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>プロパティには、1 つの日付が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="3dfb4-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>プロパティには、毎年を太字で表示される日付が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="3dfb4-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>プロパティには、すべての月を太字で表示される日付が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="3dfb4-109">これらの各プロパティの配列を含む<xref:System.DateTime>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="3dfb4-110">を追加またはこれらの一覧から日付を削除するには、追加または削除する必要があります、<xref:System.DateTime>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="3dfb4-111">日付を太字で表示するには</span><span class="sxs-lookup"><span data-stu-id="3dfb4-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="3dfb4-112">作成、<xref:System.DateTime>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2.  <span data-ttu-id="3dfb4-113">呼び出して 1 つの日付を太字、 <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>、 <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>、または<xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A>のメソッド、<xref:System.Windows.Forms.MonthCalendar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="3dfb4-114">または</span><span class="sxs-lookup"><span data-stu-id="3dfb4-114">–or–</span></span>  
  
     <span data-ttu-id="3dfb4-115">日付のセットを太字に一度にすべての配列を作成することで<xref:System.DateTime>オブジェクトおよびプロパティのいずれかに割り当てるとします。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="3dfb4-116">日付を通常のフォントで表示するには</span><span class="sxs-lookup"><span data-stu-id="3dfb4-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="3dfb4-117">1 つの太字で表示される日付を呼び出すことによって通常フォントで表示、 <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>、 <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>、または<xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="3dfb4-118">または</span><span class="sxs-lookup"><span data-stu-id="3dfb4-118">–or–</span></span>  
  
     <span data-ttu-id="3dfb4-119">3 つのリストのいずれかから呼び出すことによって、太字で表示される日付をすべてを削除、 <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>、 <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>、または<xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="3dfb4-120">呼び出して、フォントの外観を更新、<xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3dfb4-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3dfb4-121">参照</span><span class="sxs-lookup"><span data-stu-id="3dfb4-121">See Also</span></span>  
 [<span data-ttu-id="3dfb4-122">MonthCalendar コントロール</span><span class="sxs-lookup"><span data-stu-id="3dfb4-122">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="3dfb4-123">方法: Windows フォームの MonthCalendar コントロールで日付の範囲を選択する</span><span class="sxs-lookup"><span data-stu-id="3dfb4-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="3dfb4-124">方法: Windows フォームの MonthCalendar コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="3dfb4-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="3dfb4-125">方法: Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する</span><span class="sxs-lookup"><span data-stu-id="3dfb4-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
