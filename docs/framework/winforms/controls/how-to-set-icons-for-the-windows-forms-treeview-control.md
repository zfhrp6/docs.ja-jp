---
title: "方法 : Windows フォーム TreeView コントロールのアイコンを設定する | Microsoft Docs"
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
  - "アイコン, 設定 (TreeView コントロールの)"
  - "ImageList コンポーネント [Windows フォーム], 追加 (イメージを)"
  - "ツリー ノード (TreeView コントロールの), アイコン"
  - "TreeView コントロール [Windows フォーム], ノード アイコン"
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : Windows フォーム TreeView コントロールのアイコンを設定する
Windows フォーム <xref:System.Windows.Forms.TreeView> \(ツリー ビュー\) コントロールでは、各ノードの横にアイコンを表示できます。  アイコンは、ノードのテキストのすぐ左に表示されます。  アイコンを表示するには、ツリー ビューに <xref:System.Windows.Forms.ImageList> コントロールを関連付ける必要があります。  イメージ リストの詳細については、「[ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)」および「[方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)」を参照してください。  
  
> [!NOTE]
>  .NET Framework Version 1.1 のバグによって、アプリケーションから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> を呼び出すときに、画像が <xref:System.Windows.Forms.TreeView> ノードに表示されません。  このバグに対処するには、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A> の呼び出し直後に `Main` メソッドで <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> を呼び出します。  このバグは、[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] で修正されています。  
  
### ツリー ビューにイメージを表示するには  
  
1.  <xref:System.Windows.Forms.TreeView> コントロールの <xref:System.Windows.Forms.TreeView.ImageList%2A> プロパティを使用する既存の <xref:System.Windows.Forms.ImageList> コントロールに設定します。  
  
     これらのプロパティは、デザイナーの \[プロパティ\] ウィンドウで設定するか、またはコードで設定できます。  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  ノードの <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> プロパティと <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> を設定します。  <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> プロパティは、ノードが通常の状態のときや展開された状態のときに表示されるイメージを決定します。<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> プロパティは、ノードが選択された状態のときに表示されるイメージを決定します。  
  
     これらのプロパティは、コードで設定するか、または TreeNode エディターで設定できます。  TreeNode エディターを開くには、\[プロパティ\] ウィンドウの <xref:System.Windows.Forms.TreeView.Nodes%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## 参照  
 [TreeView コントロールの概要](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TreeView コントロールでノードを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)   
 [方法 : Windows フォーム TreeView コントロールのすべてのノードを反復処理する](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [方法 : クリックされた TreeView ノードを判別する](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)