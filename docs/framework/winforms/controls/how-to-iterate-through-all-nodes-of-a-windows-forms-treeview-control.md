---
title: "方法 : Windows フォーム TreeView コントロールのすべてのノードを反復処理する"
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
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 057612bfb28333df0aebaa5ca19555f4c4951687
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="23dd2-102">方法 : Windows フォーム TreeView コントロールのすべてのノードを反復処理する</span><span class="sxs-lookup"><span data-stu-id="23dd2-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="23dd2-103">Windows フォーム内の各ノードをチェックすると役立つ場合があります<xref:System.Windows.Forms.TreeView>ノードの値に対していくつか計算を実行するために管理します。</span><span class="sxs-lookup"><span data-stu-id="23dd2-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="23dd2-104">この操作は、ツリーの各コレクションの各ノードを反復処理する再帰プロシージャ (C# および C++ の場合は再帰メソッド) を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="23dd2-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="23dd2-105">各<xref:System.Windows.Forms.TreeNode>ツリー ビュー内のオブジェクトは、ツリー ビューの移動に使用できるプロパティ: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>、 <xref:System.Windows.Forms.TreeNode.LastNode%2A>、 <xref:System.Windows.Forms.TreeNode.NextNode%2A>、 <xref:System.Windows.Forms.TreeNode.PrevNode%2A>、および<xref:System.Windows.Forms.TreeNode.Parent%2A>です。</span><span class="sxs-lookup"><span data-stu-id="23dd2-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="23dd2-106">値、<xref:System.Windows.Forms.TreeNode.Parent%2A>プロパティの現在のノードの親ノードです。</span><span class="sxs-lookup"><span data-stu-id="23dd2-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="23dd2-107">現在のノードの子ノードは、いずれかを使用する必要がある場合で表示されます、<xref:System.Windows.Forms.TreeNode.Nodes%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="23dd2-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="23dd2-108"><xref:System.Windows.Forms.TreeView>コントロール自体が、<xref:System.Windows.Forms.TreeView.TopNode%2A>プロパティで、全体のツリー ビューのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="23dd2-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="23dd2-109">TreeView コントロールのすべてのノードを反復処理するには</span><span class="sxs-lookup"><span data-stu-id="23dd2-109">To iterate through all nodes of the TreeView control</span></span>  
  
1.  <span data-ttu-id="23dd2-110">各ノードをテストする再帰プロシージャ (C# および C++ における再帰メソッド) を作成します。</span><span class="sxs-lookup"><span data-stu-id="23dd2-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2.  <span data-ttu-id="23dd2-111">プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="23dd2-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="23dd2-112">次の例は、それぞれを印刷する方法を示しています。<xref:System.Windows.Forms.TreeNode>オブジェクトの<xref:System.Windows.Forms.TreeNode.Text%2A>プロパティ。</span><span class="sxs-lookup"><span data-stu-id="23dd2-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23dd2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="23dd2-113">See Also</span></span>  
 [<span data-ttu-id="23dd2-114">TreeView コントロール</span><span class="sxs-lookup"><span data-stu-id="23dd2-114">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="23dd2-115">再帰プロシージャ</span><span class="sxs-lookup"><span data-stu-id="23dd2-115">Recursive Procedures</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
