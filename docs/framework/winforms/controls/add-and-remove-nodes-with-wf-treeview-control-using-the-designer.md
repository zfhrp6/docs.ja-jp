---
title: "方法 : デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する
Windows フォームの <xref:System.Windows.Forms.TreeView> コントロールはノードを階層的に表示するため、ノードを追加するときには、どのノードを親ノードにするのかを考慮する必要があります。  
  
 次の手順では、<xref:System.Windows.Forms.TreeView> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーでノードを追加または削除するには  
  
1.  <xref:System.Windows.Forms.TreeView> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.TreeView.Nodes%2A> プロパティの横にある**省略記号** \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックします。  
  
     **TreeNode エディター**が表示されます。  
  
3.  ノードを追加するには、ルート ノードが存在している必要があります。ルート ノードが存在しない場合は、まず **\[ルートの追加\]** をクリックしてルートを追加します。  次に、ルートまたはその他のノードを選択して **\[子の追加\]** をクリックし、子ノードを追加します。  
  
4.  ノードを削除するには、削除するノードを選択し、**\[削除\]** をクリックします。  
  
## 参照  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [TreeView コントロールの概要](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TreeView コントロールのアイコンを設定する](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)   
 [方法 : Windows フォーム TreeView コントロールのすべてのノードを反復処理する](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [方法 : クリックされた TreeView ノードを判別する](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)