---
title: '方法 : ショートカット メニューを TreeView ノードに追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: 737e74184b0763ed84b4e585f2508d69944d0e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528221"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>方法 : ショートカット メニューを TreeView ノードに追加する
Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールは、ファイルや Windows エクスプ ローラーの左側のウィンドウに表示されるフォルダーと同様に、ノードの階層を表示します。 設定して、<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>プロパティに提供できる状況依存の操作、ユーザーを右クリックすると、<xref:System.Windows.Forms.TreeView>コントロール。 関連付けることにより、<xref:System.Windows.Forms.ContextMenuStrip>個人と共にコンポーネント<xref:System.Windows.Forms.TreeNode>項目にショートカット メニューの機能レベルをカスタマイズを追加することができます、<xref:System.Windows.Forms.TreeView>コントロール。  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>プログラムで TreeNode にショートカット メニューを関連付ける  
  
1.  インスタンスを作成、<xref:System.Windows.Forms.TreeView>適切なプロパティの設定でコントロールをルートを作成<xref:System.Windows.Forms.TreeNode>サブノードを追加します。  
  
2.  インスタンスを作成、<xref:System.Windows.Forms.ContextMenuStrip>コンポーネント、し、追加、<xref:System.Windows.Forms.ToolStripMenuItem>の各操作の実行時に使用できるようにします。  
  
3.  設定、 <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> 、適切なプロパティ<xref:System.Windows.Forms.TreeNode>ショートカット メニューを作成します。  
  
4.  このプロパティが設定されている場合、ノードを右クリックすると、ショートカット メニューが表示されます。  
  
 次のコード例を作成、基本的な<xref:System.Windows.Forms.TreeView>と<xref:System.Windows.Forms.ContextMenuStrip>ルートに関連付けられている<xref:System.Windows.Forms.TreeNode>の<xref:System.Windows.Forms.TreeView>です。 メニューの選択肢に一致するものをカスタマイズする必要があります、<xref:System.Windows.Forms.TreeView>を開発します。 さらを処理するコードを書き込む場合は、<xref:System.Windows.Forms.ToolStripItem.Click>これらのメニュー項目のイベントです。  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
