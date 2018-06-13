---
title: '方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える'
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: 8b8f9c7ad0ad7d3bbb7f3eeffd44e555207b82c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535647"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="cfc86-102">方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える</span><span class="sxs-lookup"><span data-stu-id="cfc86-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="cfc86-103">Windows フォーム コントロールには、データ バインドがあるときに並べ替えられません。</span><span class="sxs-lookup"><span data-stu-id="cfc86-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="cfc86-104">並べ替え済みのデータを表示するには、並べ替えをサポートするデータ ソースを使用して、並べ替えられて、データ ソース。</span><span class="sxs-lookup"><span data-stu-id="cfc86-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="cfc86-105">並べ替えをサポートするデータ ソースのデータ ビューは、データのビュー マネージャー、および並べ替えられた配列。</span><span class="sxs-lookup"><span data-stu-id="cfc86-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="cfc86-106">コントロールがデータ バインドでない場合は、それを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="cfc86-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="cfc86-107">一覧を並べ替える</span><span class="sxs-lookup"><span data-stu-id="cfc86-107">To sort the list</span></span>  
  
1.  <span data-ttu-id="cfc86-108">`Sorted` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="cfc86-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="cfc86-109">この設定は、並べ替え順序ですべての既存のリスト アイテムを再配置します。</span><span class="sxs-lookup"><span data-stu-id="cfc86-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc86-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfc86-110">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="cfc86-111">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="cfc86-111">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="cfc86-112">方法: Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する</span><span class="sxs-lookup"><span data-stu-id="cfc86-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="cfc86-113">ListBox の代わりに Windows フォーム ComboBox を使用する場合</span><span class="sxs-lookup"><span data-stu-id="cfc86-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="cfc86-114">オプションのリストを表示するための Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="cfc86-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
