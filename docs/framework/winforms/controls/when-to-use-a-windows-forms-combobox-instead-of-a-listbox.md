---
title: ListBox の代わりに Windows フォーム ComboBox を使用する場合
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 88b6a6023fbfdd8fa315fcd434357626ea69a9ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537769"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="dc440-102">ListBox の代わりに Windows フォーム ComboBox を使用する場合</span><span class="sxs-lookup"><span data-stu-id="dc440-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="dc440-103"><xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.ListBox>コントロール似たような動作は、でき、場合によっては同義です。</span><span class="sxs-lookup"><span data-stu-id="dc440-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="dc440-104">ただしが 1 つまたはもう一方のタスクをより適切な時間があります。</span><span class="sxs-lookup"><span data-stu-id="dc440-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="dc440-105">一般に、コンボ ボックスが適して、推奨される選択肢の一覧があるし、リスト ボックスは、一覧にあるものへの入力を制限する場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="dc440-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="dc440-106">コンボ ボックスには、一覧にない値を入力するためのテキスト ボックスのフィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc440-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="dc440-107">例外は、<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>プロパティに設定されている<xref:System.Windows.Forms.ComboBoxStyle.DropDownList>です。</span><span class="sxs-lookup"><span data-stu-id="dc440-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="dc440-108">その場合は、コントロールが選択項目の最初の文字を入力するされます。</span><span class="sxs-lookup"><span data-stu-id="dc440-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="dc440-109">さらに、コンボ ボックスは、フォームの領域を節約します。</span><span class="sxs-lookup"><span data-stu-id="dc440-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="dc440-110">下向きの矢印をクリックするまでに、完全な一覧が表示されていないために、コンボ ボックスは、リスト ボックスが収まらない小さなスペースに簡単に適合できます。</span><span class="sxs-lookup"><span data-stu-id="dc440-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="dc440-111">ときに例外が、<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>プロパティに設定されている<xref:System.Windows.Forms.ComboBoxStyle.Simple>: 完全な一覧が表示され、コンボ ボックスは、リスト ボックスの場合よりもさらにスペースを占有します。</span><span class="sxs-lookup"><span data-stu-id="dc440-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc440-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc440-112">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="dc440-113">方法: Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する</span><span class="sxs-lookup"><span data-stu-id="dc440-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="dc440-114">方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える</span><span class="sxs-lookup"><span data-stu-id="dc440-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="dc440-115">オプションのリストを表示するための Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="dc440-115">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
