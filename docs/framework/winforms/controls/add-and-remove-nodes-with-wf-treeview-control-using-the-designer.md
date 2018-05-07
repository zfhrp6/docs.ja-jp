---
title: '方法 : デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 2bf62601ae2257a098be0dc5c2cf8b5b1ba2b618
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>方法 : デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する
Windows フォームため<xref:System.Windows.Forms.TreeView>コントロールは、その親ノードに注意を払う必要があります、ノードを追加するときに、階層状にノードを表示します。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.TreeView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>追加またはデザイナーでのノードを削除するには  
  
1.  <xref:System.Windows.Forms.TreeView> コントロールを選択します。  
  
2.  **プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.TreeView.Nodes%2A>プロパティです。  
  
     **TreeNode エディター**が表示されます。  
  
3.  ノードを追加するには、ルート ノードが存在する必要があります。クリックしてルートを追加する必要がありますまず 1 つが存在しない場合、**ルートの追加**ボタンをクリックします。 ルートまたはその他のノードを選択しをクリックすると、子ノードを追加することができますし、**子の追加**ボタンをクリックします。  
  
4.  ノードを削除するを削除し、をクリックするノードを選択、**削除**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView コントロールの概要](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [方法: Windows フォーム TreeView コントロールのアイコンを設定する](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理する](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [方法: クリックされた TreeView ノードを判別する](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
