---
title: "TreeView コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TreeView
helpviewer_keywords: TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee285a7db058cd88843eb3addf207fb5c446dfa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.TreeView> コントロールでは、Windows オペレーティング システムの Windows エクスプローラーの左側のウィンドウにファイルやフォルダーが表示されるのと同じように、ノードの階層をユーザーに表示することができます。 ツリー ビュー内の各ノードと呼ばれるその他のノードを含む可能性があります*子ノード*です。 親ノード、または子ノードを含むノードを展開または折りたたんで表示できます。 また、ツリー ビューの <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> プロパティを `true` に設定することで、ノードの横にチェック ボックスがあるツリー ビューを表示することもできます。 ノードの <xref:System.Windows.Forms.TreeNode.Checked%2A> プロパティを `true` または `false` に設定することにより、プログラムでノードをオンまたはオフにすることができます。  
  
## <a name="key-properties"></a>主要プロパティ  
 <xref:System.Windows.Forms.TreeView> コントロールの主要プロパティは、<xref:System.Windows.Forms.TreeView.Nodes%2A> および <xref:System.Windows.Forms.TreeView.SelectedNode%2A> です。 <xref:System.Windows.Forms.TreeView.Nodes%2A> プロパティには、ツリー ビューの最上位のノードの一覧が含まれています。 <xref:System.Windows.Forms.TreeView.SelectedNode%2A> プロパティは、現在選択されているノードを設定します。 ノードの横にあるアイコンを表示することができます。 コントロールはツリー ビューの <xref:System.Windows.Forms.TreeView.ImageList%2A> プロパティで <xref:System.Windows.Forms.ImageList> という名前のイメージを使用します。 <xref:System.Windows.Forms.TreeView.ImageIndex%2A> プロパティは、ツリー ビューでノードの既定のイメージを設定します。 イメージの表示の詳細については、次を参照してください。[する方法: Windows フォーム TreeView コントロールの設定を示すアイコン](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)です。 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] を使用している場合は、<xref:System.Windows.Forms.TreeView> コントロールによって使用できる標準のイメージの大規模なライブラリにアクセスできます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TreeView>  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [方法: Windows フォーム TreeView コントロールのアイコンを設定する](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [方法: Windows フォーム TreeView コントロールでノードを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理する](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [方法: クリックされた TreeView ノードを判別する](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
