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
ms.openlocfilehash: 4ab73f6e4dc6a4e348853183046db564e748360b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>方法 : デザイナーを使用して TreeNode にショートカット メニューを割り当てる
Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールは、ファイルと Windows オペレーティング システムで Windows Explorer の機能の左側のウィンドウに表示されるフォルダと同様に、ノードの階層を表示します。 設定して、<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>プロパティに提供できる状況依存の操作、ユーザーを右クリックすると、<xref:System.Windows.Forms.TreeView>コントロール。 関連付けることにより、<xref:System.Windows.Forms.ContextMenuStrip>個人と共にコンポーネント<xref:System.Windows.Forms.TreeNode>項目にショートカット メニューの機能レベルをカスタマイズを追加することができます、<xref:System.Windows.Forms.TreeView>コントロール。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>デザイン時に TreeNode にショートカット メニューを関連付ける  
  
1.  追加、<xref:System.Windows.Forms.TreeView>をフォームに制御し、ノードを追加し、<xref:System.Windows.Forms.TreeView>に応じて。 詳細については、次を参照してください。[する方法: 追加および Windows フォーム TreeView コントロールでノードを削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)です。  
  
2.  追加、<xref:System.Windows.Forms.ContextMenuStrip>コンポーネントをフォームにし、実行時に使用できるようにしたいノード レベルの操作を表すショートカット メニューにメニュー項目を追加します。 詳細については、次を参照してください。[する方法: メニュー項目を ContextMenuStrip に追加](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)です。  
  
3.  再度開いて、 **TreeNodeEditor**のダイアログ ボックス、<xref:System.Windows.Forms.TreeView>制御、編集、および設定するノードを選択、<xref:System.Windows.Forms.ContextMenuStrip>プロパティを追加したショートカット メニューをします。  
  
4.  このプロパティが設定されている場合、ノードを右クリックすると、ショートカット メニューが表示されます。  
  
     さらを処理するコードを書き込む場合は、<xref:System.Windows.Forms.ToolStripItem.Click>これらのメニュー項目のイベントです。  
  
## <a name="see-also"></a>参照  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView コントロールの概要](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [ContextMenuStrip コントロール](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
