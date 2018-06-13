---
title: '方法 : Windows フォーム ListView コントロールのアイコンを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 0e597ed182739947014b4f405ee2dc3149b62849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533605"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="915cf-102">方法 : Windows フォーム ListView コントロールのアイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="915cf-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="915cf-103">Windows フォーム<xref:System.Windows.Forms.ListView>コントロールは、次の 3 つのイメージ リストのアイコンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="915cf-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="915cf-104">リスト、詳細、および SmallIcon ビューで指定されたイメージ リストのイメージを表示する、<xref:System.Windows.Forms.ListView.SmallImageList%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="915cf-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="915cf-105">LargeIcon ビューで指定されたイメージ リストのイメージを表示する、<xref:System.Windows.Forms.ListView.LargeImageList%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="915cf-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="915cf-106">リスト ビューでは、追加で設定アイコンのセットを表示できますも、<xref:System.Windows.Forms.ListView.StateImageList%2A>プロパティを大きいアイコンまたは小さいアイコンの横にあります。</span><span class="sxs-lookup"><span data-stu-id="915cf-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="915cf-107">イメージ リストの詳細については、次を参照してください。 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)と[する方法: 追加または削除する Windows フォームの ImageList コンポーネントにイメージを](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)です。</span><span class="sxs-lookup"><span data-stu-id="915cf-107">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="915cf-108">リスト ビュー内のイメージを表示するには</span><span class="sxs-lookup"><span data-stu-id="915cf-108">To display images in a list view</span></span>  
  
1.  <span data-ttu-id="915cf-109">適切なプロパティを設定する —<xref:System.Windows.Forms.ListView.SmallImageList%2A>、 <xref:System.Windows.Forms.ListView.LargeImageList%2A>、または<xref:System.Windows.Forms.ListView.StateImageList%2A>— を既存<xref:System.Windows.Forms.ImageList>コンポーネントを使用する場合します。</span><span class="sxs-lookup"><span data-stu-id="915cf-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="915cf-110">デザイナーの [プロパティ] ウィンドウまたはコードでは、これらのプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="915cf-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  <span data-ttu-id="915cf-111">設定、<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>または<xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A>アイコンが関連付けられている各リスト項目のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="915cf-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="915cf-112">コードでは、内、またはこれらのプロパティを設定することができます、 **ListViewItem コレクション エディター**です。</span><span class="sxs-lookup"><span data-stu-id="915cf-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="915cf-113">開くには、 **ListViewItem コレクション エディター**、省略記号ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton"))、の横にある<xref:System.Windows.Forms.ListView.Items%2A>プロパティを**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="915cf-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="915cf-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="915cf-114">See Also</span></span>  
 [<span data-ttu-id="915cf-115">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="915cf-115">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="915cf-116">方法: Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="915cf-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="915cf-117">方法: Windows フォーム ListView コントロールに列を追加する</span><span class="sxs-lookup"><span data-stu-id="915cf-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="915cf-118">方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="915cf-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [<span data-ttu-id="915cf-119">ImageList コンポーネント</span><span class="sxs-lookup"><span data-stu-id="915cf-119">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
