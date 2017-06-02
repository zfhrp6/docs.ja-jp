---
title: "方法 : Windows フォーム TreeView コントロールでノードを追加および削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "例 [Windows フォーム], TreeView コントロール"
  - "ツリー ノード (TreeView コントロールの)"
  - "TreeView コントロール [Windows フォーム], 追加 (ノードの)"
  - "TreeView コントロール [Windows フォーム], 削除 (ノードを)"
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム TreeView コントロールでノードを追加および削除する
Windows フォーム コントロール <xref:System.Windows.Forms.TreeView> は、最上位のノードを <xref:System.Windows.Forms.TreeView.Nodes%2A> コレクションに保存します。  各 <xref:System.Windows.Forms.TreeNode> にも子ノードを保存するための独自の <xref:System.Windows.Forms.TreeNode.Nodes%2A> コレクションがあります。  両方のコレクションのプロパティが <xref:System.Windows.Forms.TreeNodeCollection> 型であり、ノード階層の単一のレベルでノードを追加、削除、および再配置するために使用できる標準のコレクション メンバーが用意されています。  
  
### プログラムによってノードを追加するには  
  
1.  ツリー ビューの <xref:System.Windows.Forms.TreeView.Nodes%2A> プロパティの <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> メソッドを使用します。  
  
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
  
### プログラムによってノードを削除するには  
  
1.  ツリー ビューの <xref:System.Windows.Forms.TreeView.Nodes%2A> プロパティの <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> メソッドを使用して 1 つのノードを削除するか、または <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> メソッドを使用してすべてのノードを削除します。  
  
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
  
## 参照  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [TreeView コントロールの概要](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TreeView コントロールのアイコンを設定する](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)   
 [方法 : Windows フォーム TreeView コントロールのすべてのノードを反復処理する](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [方法 : クリックされた TreeView ノードを判別する](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)