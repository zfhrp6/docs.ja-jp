---
title: "方法 : デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f6295f915e9204e9996d8902b07a3dfc4c5c2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="9ecc1-102">方法 : デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="9ecc1-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="9ecc1-103">Windows フォームため<xref:System.Windows.Forms.TreeView>コントロールは、その親ノードに注意を払う必要があります、ノードを追加するときに、階層状にノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="9ecc1-104">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.TreeView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="9ecc1-105">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-105">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ecc1-106">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9ecc1-107">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9ecc1-108">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="9ecc1-109">追加またはデザイナーでのノードを削除するには</span><span class="sxs-lookup"><span data-stu-id="9ecc1-109">To add or remove nodes in the designer</span></span>  
  
1.  <span data-ttu-id="9ecc1-110"><xref:System.Windows.Forms.TreeView> コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2.  <span data-ttu-id="9ecc1-111">**プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.TreeView.Nodes%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="9ecc1-112">**TreeNode エディター**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-112">The **TreeNode Editor** appears.</span></span>  
  
3.  <span data-ttu-id="9ecc1-113">ノードを追加するには、ルート ノードが存在する必要があります。クリックしてルートを追加する必要がありますまず 1 つが存在しない場合、**ルートの追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="9ecc1-114">ルートまたはその他のノードを選択しをクリックすると、子ノードを追加することができますし、**子の追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4.  <span data-ttu-id="9ecc1-115">ノードを削除するを削除し、をクリックするノードを選択、**削除**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ecc1-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecc1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ecc1-116">See Also</span></span>  
 [<span data-ttu-id="9ecc1-117">TreeView コントロール</span><span class="sxs-lookup"><span data-stu-id="9ecc1-117">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="9ecc1-118">TreeView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="9ecc1-118">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="9ecc1-119">方法: Windows フォーム TreeView コントロールのアイコンを設定する</span><span class="sxs-lookup"><span data-stu-id="9ecc1-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="9ecc1-120">方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理する</span><span class="sxs-lookup"><span data-stu-id="9ecc1-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="9ecc1-121">方法: クリックされた TreeView ノードを判別する</span><span class="sxs-lookup"><span data-stu-id="9ecc1-121">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="9ecc1-122">方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="9ecc1-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
