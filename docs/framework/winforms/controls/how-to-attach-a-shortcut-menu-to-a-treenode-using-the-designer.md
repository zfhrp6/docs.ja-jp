---
title: "方法 : デザイナーを使用して TreeNode にショートカット メニューを割り当てる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3acc1a731fa584a17c8a96f8a02986a504cd302d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="622bf-102">方法 : デザイナーを使用して TreeNode にショートカット メニューを割り当てる</span><span class="sxs-lookup"><span data-stu-id="622bf-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="622bf-103">Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールは、ファイルと Windows オペレーティング システムで Windows Explorer の機能の左側のウィンドウに表示されるフォルダと同様に、ノードの階層を表示します。</span><span class="sxs-lookup"><span data-stu-id="622bf-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="622bf-104">設定して、<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>プロパティに提供できる状況依存の操作、ユーザーを右クリックすると、<xref:System.Windows.Forms.TreeView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="622bf-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="622bf-105">関連付けることにより、<xref:System.Windows.Forms.ContextMenuStrip>個人と共にコンポーネント<xref:System.Windows.Forms.TreeNode>項目にショートカット メニューの機能レベルをカスタマイズを追加することができます、<xref:System.Windows.Forms.TreeView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="622bf-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="622bf-106">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="622bf-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="622bf-107">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="622bf-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="622bf-108">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622bf-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="622bf-109">デザイン時に TreeNode にショートカット メニューを関連付ける</span><span class="sxs-lookup"><span data-stu-id="622bf-109">To associate a shortcut menu with a TreeNode at design time</span></span>  
  
1.  <span data-ttu-id="622bf-110">追加、<xref:System.Windows.Forms.TreeView>をフォームに制御し、ノードを追加し、<xref:System.Windows.Forms.TreeView>に応じて。</span><span class="sxs-lookup"><span data-stu-id="622bf-110">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="622bf-111">詳細については、次を参照してください。[する方法: 追加および Windows フォーム TreeView コントロールでノードを削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="622bf-111">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>  
  
2.  <span data-ttu-id="622bf-112">追加、<xref:System.Windows.Forms.ContextMenuStrip>コンポーネントをフォームにし、実行時に使用できるようにしたいノード レベルの操作を表すショートカット メニューにメニュー項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="622bf-112">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="622bf-113">詳細については、次を参照してください。[する方法: メニュー項目を ContextMenuStrip に追加](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)です。</span><span class="sxs-lookup"><span data-stu-id="622bf-113">For more information, see [How to: Add Menu Items to a ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>  
  
3.  <span data-ttu-id="622bf-114">再度開いて、 **TreeNodeEditor**のダイアログ ボックス、<xref:System.Windows.Forms.TreeView>制御、編集、および設定するノードを選択、<xref:System.Windows.Forms.ContextMenuStrip>プロパティを追加したショートカット メニューをします。</span><span class="sxs-lookup"><span data-stu-id="622bf-114">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>  
  
4.  <span data-ttu-id="622bf-115">このプロパティが設定されている場合、ノードを右クリックすると、ショートカット メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="622bf-115">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
     <span data-ttu-id="622bf-116">さらを処理するコードを書き込む場合は、<xref:System.Windows.Forms.ToolStripItem.Click>これらのメニュー項目のイベントです。</span><span class="sxs-lookup"><span data-stu-id="622bf-116">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622bf-117">参照</span><span class="sxs-lookup"><span data-stu-id="622bf-117">See Also</span></span>  
 [<span data-ttu-id="622bf-118">TreeView コントロール</span><span class="sxs-lookup"><span data-stu-id="622bf-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="622bf-119">TreeView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="622bf-119">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="622bf-120">ContextMenuStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="622bf-120">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
