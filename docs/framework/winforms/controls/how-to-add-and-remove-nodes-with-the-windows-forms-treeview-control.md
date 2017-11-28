---
title: "方法 : Windows フォーム TreeView コントロールでノードを追加および削除する"
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
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41834f0bdfe800019c1f641d5b20147b10774221
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="3367b-102">方法 : Windows フォーム TreeView コントロールでノードを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="3367b-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="3367b-103">Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールは、最上位のノードを保存します。 その<xref:System.Windows.Forms.TreeView.Nodes%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="3367b-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="3367b-104">各<xref:System.Windows.Forms.TreeNode>も独自<xref:System.Windows.Forms.TreeNode.Nodes%2A>をその子ノードを格納するコレクション。</span><span class="sxs-lookup"><span data-stu-id="3367b-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="3367b-105">型の両方のコレクション プロパティは、 <xref:System.Windows.Forms.TreeNodeCollection>、標準コレクション メンバーを追加、削除、およびノード階層の 1 つのレベルのノードを再配置を提供します。</span><span class="sxs-lookup"><span data-stu-id="3367b-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="3367b-106">プログラムでノードを追加するには</span><span class="sxs-lookup"><span data-stu-id="3367b-106">To add nodes programmatically</span></span>  
  
1.  <span data-ttu-id="3367b-107">使用して、<xref:System.Windows.Forms.TreeNodeCollection.Add%2A>のツリー ビューのメソッド<xref:System.Windows.Forms.TreeView.Nodes%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3367b-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="3367b-108">プログラムでノードを削除するには</span><span class="sxs-lookup"><span data-stu-id="3367b-108">To remove nodes programmatically</span></span>  
  
1.  <span data-ttu-id="3367b-109">使用して、<xref:System.Windows.Forms.TreeNodeCollection.Remove%2A>のツリー ビューのメソッド<xref:System.Windows.Forms.TreeView.Nodes%2A>1 つのノードを削除するプロパティまたは<xref:System.Windows.Forms.TreeNodeCollection.Clear%2A>メソッドのすべてのノードをオフにします。</span><span class="sxs-lookup"><span data-stu-id="3367b-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3367b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="3367b-110">See Also</span></span>  
 [<span data-ttu-id="3367b-111">TreeView コントロール</span><span class="sxs-lookup"><span data-stu-id="3367b-111">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="3367b-112">TreeView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="3367b-112">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="3367b-113">方法: Windows フォーム TreeView コントロールのアイコンを設定する</span><span class="sxs-lookup"><span data-stu-id="3367b-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="3367b-114">方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理する</span><span class="sxs-lookup"><span data-stu-id="3367b-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="3367b-115">方法: クリックされた TreeView ノードを判別する</span><span class="sxs-lookup"><span data-stu-id="3367b-115">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="3367b-116">方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="3367b-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
