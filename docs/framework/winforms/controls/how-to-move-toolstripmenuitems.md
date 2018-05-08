---
title: '方法 : ToolStripMenuItems を移動する'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: 5cfaf87a59d27678cfb786633ed4c9a9f66bac76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-move-toolstripmenuitems"></a>方法 : ToolStripMenuItems を移動する
デザイン時に行うことができますトップレベル メニュー全体とそのメニュー項目を別の場所、<xref:System.Windows.Forms.MenuStrip>です。 トップレベル メニュー間で個々 のメニュー項目を移動したり、メニュー内のメニュー項目の位置を変更できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>トップレベル メニューとそのメニュー項目を最上位レベルの別の場所に移動するには  
  
1.  クリックして、移動するメニューにマウスの左ボタンを押したままにします。  
  
2.  前となる新しい場所にあるトップレベルのメニューにカーソルをドラッグし、マウスの左ボタンを離します。  
  
     選択されたメニューは、カーソルの右側に移動します。  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>トップレベル メニューとそのメニュー項目をドロップダウンの場所に移動するには  
  
1.  移動、ctrl キーを押しながら X キーを押すかメニューを右クリックして、選択するメニューを左クリックして**切り取り**ショートカット メニューからです。  
  
2.  宛先のトップレベル メニューで、メニュー項目となる新しい場所の上をクリックして、ctrl キーを押しながら V キーを押しますまたはとなる新しい場所の上のメニュー項目を右クリックし、選択**貼り付け**ショートカット メニューからです。  
  
     切り取ったメニューは、選択されたメニュー項目の後に挿入されます。  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Items コレクション エディターを使用してメニュー内のメニュー項目を移動するには  
  
1.  移動するメニュー項目が含まれているメニューを右クリックします。  
  
2.  ショートカット メニューから選択**ドロップダウン項目の編集**です。  
  
3.  **Items コレクション エディター**に移動するメニュー項目を左クリックします。  
  
4.  メニュー内のメニュー項目を移動する上下矢印キーをクリックします。  
  
5.  **[OK]** をクリックします。  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>キーボードを使用してメニュー内のメニュー項目を移動するには  
  
1.  キーを押して、ALT キーを押したままにします。  
  
2.  移動するメニュー項目をマウスの左ボタンを押したままにします。  
  
3.  メニュー項目を新しい場所にドラッグし、マウスの左ボタンを離します。  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>別のメニューにメニュー項目を移動するには  
  
1.  移動および ctrl キーを押しながら X キーを押しますまたはメニュー項目を右クリックしを選択するメニュー項目を左クリックして**切り取り**ショートカット メニューからです。  
  
2.  メニュー項目を格納するメニューをクリックしてください。  
  
3.  前となる新しい場所にあるメニュー項目を左クリックし、ctrl キーを押しながら V キーを押してまたはメニュー項目となる新しい場所を選択する前にを右クリックして**貼り付け**ショートカット メニューからです。  
  
     切り取りするメニュー項目が選択されたメニュー項目の後に挿入されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
