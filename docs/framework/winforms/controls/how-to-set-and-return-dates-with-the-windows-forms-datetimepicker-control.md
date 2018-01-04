---
title: "方法 : Windows フォームの DateTimePicker コントロールを使用して日付を設定および取得する"
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
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83a95d2c1aa9f1704f143ae9095cb38596d2c1a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="28b38-102">方法 : Windows フォームの DateTimePicker コントロールを使用して日付を設定および取得する</span><span class="sxs-lookup"><span data-stu-id="28b38-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="28b38-103">Windows フォーム <xref:System.Windows.Forms.DateTimePicker> コントロールで現在選択されている日付または時刻は、<xref:System.Windows.Forms.DateTimePicker.Value%2A> プロパティによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="28b38-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="28b38-104">コントロールが表示される前 (デザイン時またはフォームの <xref:System.Windows.Forms.Form.Load> イベントなど) に <xref:System.Windows.Forms.DateTimePicker.Value%2A> プロパティを設定して、コントロールで最初に選択される日付を決定します。</span><span class="sxs-lookup"><span data-stu-id="28b38-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="28b38-105">既定では、コントロールの <xref:System.Windows.Forms.DateTimePicker.Value%2A> は現在の日付に設定されます。</span><span class="sxs-lookup"><span data-stu-id="28b38-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="28b38-106">コントロールの <xref:System.Windows.Forms.DateTimePicker.Value%2A> をコードで変更するには、フォームでコントロールが新しい設定を反映するよう自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="28b38-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="28b38-107"><xref:System.Windows.Forms.DateTimePicker.Value%2A> プロパティは、値として <xref:System.DateTime> 構造を返します。</span><span class="sxs-lookup"><span data-stu-id="28b38-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="28b38-108">表示される日付に関する特定の情報を返す <xref:System.DateTime> 構造のプロパティはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="28b38-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="28b38-109">これらのプロパティは値を返す貯めにのみ使用でき、値の設定には使用しません。</span><span class="sxs-lookup"><span data-stu-id="28b38-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
-   <span data-ttu-id="28b38-110">日付値の場合、<xref:System.DateTime.Month%2A>、<xref:System.DateTime.Day%2A>、および <xref:System.DateTime.Year%2A> の各プロパティは、選択した日付の時間単位の整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="28b38-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="28b38-111"><xref:System.DateTime.DayOfWeek%2A> プロパティは、選択した日の曜日を示す値を返します (指定できる値は <xref:System.DayOfWeek> 列挙型にリストされます)。</span><span class="sxs-lookup"><span data-stu-id="28b38-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
-   <span data-ttu-id="28b38-112">時間値の場合、<xref:System.DateTime.Hour%2A>、<xref:System.DateTime.Minute%2A>、<xref:System.DateTime.Second%2A>、および <xref:System.DateTime.Millisecond%2A> の各プロパティは、時間単位の整数値を返します。</span><span class="sxs-lookup"><span data-stu-id="28b38-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="28b38-113">時刻を表示するコントロールを構成するのを参照してください。[する方法: DateTimePicker コントロールを使用、表示時間](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="28b38-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="28b38-114">コントロールの日付と時刻の値を設定するには</span><span class="sxs-lookup"><span data-stu-id="28b38-114">To set the date and time value of the control</span></span>  
  
-   <span data-ttu-id="28b38-115"><xref:System.Windows.Forms.DateTimePicker.Value%2A> プロパティを日付または時刻の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="28b38-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="28b38-116">日付と時刻の値を返すには</span><span class="sxs-lookup"><span data-stu-id="28b38-116">To return the date and time value</span></span>  
  
-   <span data-ttu-id="28b38-117"><xref:System.Windows.Forms.DateTimePicker.Text%2A> プロパティを呼び出して、コントロールで書式設定する全体の値を返すか、または <xref:System.Windows.Forms.DateTimePicker.Value%2A> プロパティの適切なメソッドを呼び出して、値の一部を返します。</span><span class="sxs-lookup"><span data-stu-id="28b38-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="28b38-118"><xref:System.Windows.Forms.DateTimePicker.ToString%2A> を使用して、ユーザーに表示される文字列に情報を変換します。</span><span class="sxs-lookup"><span data-stu-id="28b38-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",   
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",   
       DateTimePicker1.Value.Millisecond.ToString)  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +   
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +   
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +   
       dateTimePicker1.Value.Millisecond.ToString());  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="28b38-119">参照</span><span class="sxs-lookup"><span data-stu-id="28b38-119">See Also</span></span>  
 [<span data-ttu-id="28b38-120">DateTimePicker コントロール</span><span class="sxs-lookup"><span data-stu-id="28b38-120">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="28b38-121">方法: Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する</span><span class="sxs-lookup"><span data-stu-id="28b38-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
