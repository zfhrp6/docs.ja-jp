---
title: '方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: efee926301bc358bb7645ba67826f412c0d0dbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="be0d5-102">方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する</span><span class="sxs-lookup"><span data-stu-id="be0d5-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="be0d5-103">Windows フォーム<xref:System.Windows.Forms.ListView>コントロールは、追加のテキスト、または詳細ビュー内の各項目のサブ項目を表示できます。</span><span class="sxs-lookup"><span data-stu-id="be0d5-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="be0d5-104">最初の列には、たとえば社員数、項目のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="be0d5-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="be0d5-105">2 番目、3 番目、およびそれ以降の列に、最初は第 2 に、表示し、後続の関連するサブ項目です。</span><span class="sxs-lookup"><span data-stu-id="be0d5-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="be0d5-106">リスト項目にサブ項目を追加するには</span><span class="sxs-lookup"><span data-stu-id="be0d5-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="be0d5-107">必要なすべての列を追加します。</span><span class="sxs-lookup"><span data-stu-id="be0d5-107">Add any columns needed.</span></span> <span data-ttu-id="be0d5-108">最初の列は、項目の表示されるため<xref:System.Windows.Forms.ListView.Text%2A>プロパティ、する必要がありますが、サブ項目よりも 1 つ以上の列です。</span><span class="sxs-lookup"><span data-stu-id="be0d5-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="be0d5-109">列を追加する方法については、次を参照してください。[する方法: Windows フォーム ListView コントロールに列の追加](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="be0d5-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="be0d5-110">呼び出す、<xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A>メソッドによって返されるコレクションの<xref:System.Windows.Forms.ListViewItem.SubItems%2A>項目のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="be0d5-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="be0d5-111">次のコード例では、employee name フィールドとリスト アイテムの部門を設定します。</span><span class="sxs-lookup"><span data-stu-id="be0d5-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="be0d5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="be0d5-112">See Also</span></span>  
 [<span data-ttu-id="be0d5-113">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="be0d5-113">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="be0d5-114">方法: Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="be0d5-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="be0d5-115">方法: Windows フォーム ListView コントロールに列を追加する</span><span class="sxs-lookup"><span data-stu-id="be0d5-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="be0d5-116">方法: Windows フォーム ListView コントロールのアイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="be0d5-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="be0d5-117">方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="be0d5-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
