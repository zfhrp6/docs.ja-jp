---
title: '方法 : Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: 2f563b5de9b80dab2af00290e8a6b3b309410a9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526010"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="104de-102">方法 : Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する</span><span class="sxs-lookup"><span data-stu-id="104de-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="104de-103">Windows フォーム<xref:System.Windows.Forms.DateTimePicker>コントロール柔軟にコントロールにおける日付と時刻の表示の書式設定します。</span><span class="sxs-lookup"><span data-stu-id="104de-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="104de-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A>プロパティに表示される定義済みの形式から選択することができます、<xref:System.Windows.Forms.DateTimePickerFormat>です。</span><span class="sxs-lookup"><span data-stu-id="104de-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="104de-105">用途に合わせて適切ながない場合は、形式指定文字を使用して、独自の書式スタイルを作成できます<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>です。</span><span class="sxs-lookup"><span data-stu-id="104de-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="104de-106">カスタム書式を表示するには</span><span class="sxs-lookup"><span data-stu-id="104de-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="104de-107"><xref:System.Windows.Forms.DateTimePicker.Format%2A> プロパティを `DateTimePickerFormat.Custom` に設定します。</span><span class="sxs-lookup"><span data-stu-id="104de-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="104de-108">設定、<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>書式指定文字列にプロパティです。</span><span class="sxs-lookup"><span data-stu-id="104de-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="104de-109">テキストを書式設定された値に追加するには</span><span class="sxs-lookup"><span data-stu-id="104de-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="104de-110">"M"のような形式指定文字またはなどの区切り記号以外の任意の文字を囲む単一引用符を使用して":"です。</span><span class="sxs-lookup"><span data-stu-id="104de-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="104de-111">たとえば、次の書式指定文字列には、現在の日付形式でが表示されます。"今日: 05:30:31 金曜日 2012 年 3 月 02、"英語 (米国) カルチャ。</span><span class="sxs-lookup"><span data-stu-id="104de-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     <span data-ttu-id="104de-112">カルチャ設定に応じて、単一引用符で囲まれていない文字は変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="104de-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="104de-113">たとえば、上記の書式指定文字列には、現在の日付形式でが表示されます。"今日: 05:30:31 金曜日 2012 年 3 月 02、"英語 (米国) カルチャ。</span><span class="sxs-lookup"><span data-stu-id="104de-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="104de-114">"Hh:mm:ss"であるために区切り記号であるものではありませんので、最初のコロンが単一引用符で囲まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="104de-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="104de-115">別のカルチャでは、形式がありますとして表示されます"今日: 05.30.31 金曜日 2012 年 3 月 2 日"です。</span><span class="sxs-lookup"><span data-stu-id="104de-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="104de-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="104de-116">See Also</span></span>  
 [<span data-ttu-id="104de-117">DateTimePicker コントロール</span><span class="sxs-lookup"><span data-stu-id="104de-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="104de-118">方法: Windows フォームの DateTimePicker コントロールを使用して日付を設定および取得する</span><span class="sxs-lookup"><span data-stu-id="104de-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
