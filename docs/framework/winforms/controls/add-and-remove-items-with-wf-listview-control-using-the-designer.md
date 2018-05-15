---
title: '方法 : デザイナーで Windows フォーム ListView コントロールを使って項目を追加および削除する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 9e50283eb21a6d5dc558bed67b5fdf341dd56288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="965bd-102">方法 : デザイナーで Windows フォーム ListView コントロールを使って項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="965bd-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="965bd-103">Windows フォームに項目を追加するプロセス<xref:System.Windows.Forms.ListView>コントロールは、主にアイテムを指定して、プロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="965bd-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="965bd-104">追加またはリスト項目の削除は、いつでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="965bd-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="965bd-105">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="965bd-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="965bd-106">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="965bd-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="965bd-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="965bd-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="965bd-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="965bd-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="965bd-109">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="965bd-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="965bd-110">デザイナーを使用してアイテムを追加または削除</span><span class="sxs-lookup"><span data-stu-id="965bd-110">To add or remove items using the designer</span></span>  
  
1.  <span data-ttu-id="965bd-111"><xref:System.Windows.Forms.ListView> コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="965bd-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2.  <span data-ttu-id="965bd-112">**プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.ListView.Items%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="965bd-112">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="965bd-113">**ListViewItem コレクション エディター**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="965bd-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="965bd-114">項目を追加する をクリックして、**追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="965bd-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="965bd-115">など、新しい項目のプロパティを設定することができますし、<xref:System.Windows.Forms.ListView.Text%2A>と<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="965bd-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4.  <span data-ttu-id="965bd-116">削除する項目を選択し、クリックして、**削除**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="965bd-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="965bd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="965bd-117">See Also</span></span>  
 [<span data-ttu-id="965bd-118">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="965bd-118">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="965bd-119">方法: Windows フォーム ListView コントロールに列を追加する</span><span class="sxs-lookup"><span data-stu-id="965bd-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="965bd-120">方法: Windows フォーム ListView コントロールの列にサブ項目を表示する</span><span class="sxs-lookup"><span data-stu-id="965bd-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="965bd-121">方法: Windows フォーム ListView コントロールのアイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="965bd-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="965bd-122">方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="965bd-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [<span data-ttu-id="965bd-123">方法: Windows フォーム ListView コントロールの項目をグループ化する</span><span class="sxs-lookup"><span data-stu-id="965bd-123">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
