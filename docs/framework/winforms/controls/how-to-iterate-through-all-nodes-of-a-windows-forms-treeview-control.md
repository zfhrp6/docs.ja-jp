---
title: "方法 : Windows フォーム TreeView コントロールのすべてのノードを反復処理する | Microsoft Docs"
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
  - "ツリー ノード (TreeView コントロールの), 反復処理"
  - "TreeView コントロール [Windows フォーム], 反復処理 (ノードの)"
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム TreeView コントロールのすべてのノードを反復処理する
ノードの値について何か処理を行うために、Windows フォーム <xref:System.Windows.Forms.TreeView> コントロールのすべてのノードをチェックすると役立つことがあります。  この操作は、ツリーの各コレクションの各ノードを反復処理する再帰プロシージャ \(C\# および C\+\+ における再帰メソッド\) を使用して実行できます。  
  
 ツリー ビューの各 <xref:System.Windows.Forms.TreeNode> オブジェクトには、ツリー ビューを移動するための <xref:System.Windows.Forms.TreeNode.FirstNode%2A> プロパティ、<xref:System.Windows.Forms.TreeNode.LastNode%2A> プロパティ、<xref:System.Windows.Forms.TreeNode.NextNode%2A> プロパティ、<xref:System.Windows.Forms.TreeNode.PrevNode%2A> プロパティ、および <xref:System.Windows.Forms.TreeNode.Parent%2A> プロパティがあります。  <xref:System.Windows.Forms.TreeNode.Parent%2A> プロパティの値には、現在のノードの親ノードが設定されます。  現在のノードに子ノードがある場合は、子ノードの一覧が <xref:System.Windows.Forms.TreeNode.Nodes%2A> プロパティに表示されます。  <xref:System.Windows.Forms.TreeView> コントロール自体には、ツリー ビュー全体のルート ノードを示す <xref:System.Windows.Forms.TreeView.TopNode%2A> プロパティがあります。  
  
### TreeView コントロールのすべてのノードを反復処理するには  
  
1.  各ノードをテストする再帰プロシージャ \(C\# および C\+\+ における再帰メソッド\) を作成します。  
  
2.  プロシージャを呼び出します。  
  
     各 <xref:System.Windows.Forms.TreeNode> オブジェクトの <xref:System.Windows.Forms.TreeNode.Text%2A> プロパティを出力する例を次に示します。  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## 参照  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [Recursive Procedures](../Topic/Recursive%20Procedures%20\(Visual%20Basic\).md)