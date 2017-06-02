---
title: "方法 : クリックされた TreeView ノード (Windows フォーム) を判別する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TreeNode"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "例 [Windows フォーム], TreeView コントロール"
  - "ツリー ノード (TreeView コントロールの), 判断 (ノードのクリックを)"
  - "TreeView コントロール [Windows フォーム], 判断 (ノードのクリックを)"
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : クリックされた TreeView ノード (Windows フォーム) を判別する
Windows フォームの <xref:System.Windows.Forms.TreeView> コントロールを使用する場合に共通する作業は、クリックされたノードを判別し、適切に応答することです。  
  
### クリックされた TreeView ノードを判別するには  
  
1.  <xref:System.EventArgs> オブジェクトを使用して、クリックされたノード オブジェクトへの参照を返します。  
  
2.  イベントに関連するデータを格納している <xref:System.Windows.Forms.TreeViewEventArgs> クラスを調べて、どのノードがクリックされたかを確認します。  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Control.MouseDown> または<xref:System.Windows.Forms.Control.MouseUp> イベントの <xref:System.Windows.Forms.MouseEventArgs> を使用して、クリックされた <xref:System.Drawing.Point> の <xref:System.Drawing.Point.X%2A> 座標値と <xref:System.Drawing.Point.Y%2A> 座標値を取得することもできます。  その後で、<xref:System.Windows.Forms.TreeView> コントロールの <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> メソッドを使用して、どのノードがクリックされたかを確認します。  
  
## 参照  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)