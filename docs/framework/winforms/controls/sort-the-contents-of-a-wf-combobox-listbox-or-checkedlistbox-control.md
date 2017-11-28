---
title: "方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e43a23d632b397889721373471a8fa165052d7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="a832f-102">方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える</span><span class="sxs-lookup"><span data-stu-id="a832f-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="a832f-103">Windows フォーム コントロールには、データ バインドがあるときに並べ替えられません。</span><span class="sxs-lookup"><span data-stu-id="a832f-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="a832f-104">並べ替え済みのデータを表示するには、並べ替えをサポートするデータ ソースを使用して、並べ替えられて、データ ソース。</span><span class="sxs-lookup"><span data-stu-id="a832f-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="a832f-105">並べ替えをサポートするデータ ソースのデータ ビューは、データのビュー マネージャー、および並べ替えられた配列。</span><span class="sxs-lookup"><span data-stu-id="a832f-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="a832f-106">コントロールがデータ バインドでない場合は、それを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="a832f-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="a832f-107">一覧を並べ替える</span><span class="sxs-lookup"><span data-stu-id="a832f-107">To sort the list</span></span>  
  
1.  <span data-ttu-id="a832f-108">`Sorted` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a832f-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="a832f-109">この設定は、並べ替え順序ですべての既存のリスト アイテムを再配置します。</span><span class="sxs-lookup"><span data-stu-id="a832f-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a832f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="a832f-110">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="a832f-111">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="a832f-111">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="a832f-112">方法: Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する</span><span class="sxs-lookup"><span data-stu-id="a832f-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="a832f-113">ListBox の代わりに Windows フォーム ComboBox を使用する場合</span><span class="sxs-lookup"><span data-stu-id="a832f-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="a832f-114">オプションのリストを表示するための Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="a832f-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
