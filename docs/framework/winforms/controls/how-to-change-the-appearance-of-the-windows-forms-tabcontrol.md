---
title: '方法 : Windows フォーム TabControl の表示形式を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 1ea2208229d790f69e517d55e2de5ee042bdfb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531041"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>方法 : Windows フォーム TabControl の表示形式を変更する
プロパティを使用して Windows フォーム内のタブの外観を変更することができます、<xref:System.Windows.Forms.TabControl>と<xref:System.Windows.Forms.TabPage>コントロールの個々 のタブを構成するオブジェクト。 これらのプロパティを設定することができますタブ上のイメージを表示、水平方向にではなく垂直方向にタブが表示されます、 タブの複数の行を表示および有効または無効にタブ プログラムで。  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>タブのラベルのアイコンを表示するには  
  
1.  追加、<xref:System.Windows.Forms.ImageList>をフォームにコントロールできます。  
  
2.  イメージ リストに画像を追加します。  
  
     イメージ リストの詳細については、次を参照してください。 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)と[する方法: 追加または削除する Windows フォームの ImageList コンポーネントにイメージを](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)です。  
  
3.  設定、<xref:System.Windows.Forms.TabControl.ImageList%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>を<xref:System.Windows.Forms.ImageList>コントロール。  
  
4.  設定、<xref:System.Windows.Forms.TabPage.ImageIndex%2A>のプロパティ、<xref:System.Windows.Forms.TabPage>リスト内の適切なイメージのインデックスにします。  
  
### <a name="to-create-multiple-rows-of-tabs"></a>複数行のタブを作成するには  
  
1.  選択したタブ ページの数を追加します。  
  
2.  設定、<xref:System.Windows.Forms.TabControl.Multiline%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>に`true`です。  
  
3.  複数の行にタブは表示されていない場合は、設定、<xref:System.Windows.Forms.Control.Width%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>にすべてのタブより狭くします。  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>コントロールの横のタブを配置するには  
  
-   設定、<xref:System.Windows.Forms.TabControl.Alignment%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>に<xref:System.Windows.Forms.TabAlignment.Left>または<xref:System.Windows.Forms.TabAlignment.Right>です。  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>プログラムで有効にするにまたはタブ上のすべてのコントロールを無効にするには  
  
1.  設定、<xref:System.Windows.Forms.TabPage.Enabled%2A>のプロパティ、<xref:System.Windows.Forms.TabPage>に`true`または`false`です。  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>タブのボタンとして表示するには  
  
-   設定、<xref:System.Windows.Forms.TabControl.Appearance%2A>のプロパティ、<xref:System.Windows.Forms.TabControl>に<xref:System.Windows.Forms.TabAppearance.Buttons>または<xref:System.Windows.Forms.TabAppearance.FlatButtons>です。  
  
## <a name="see-also"></a>関連項目  
 [TabControl コントロール](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl コントロールの概要](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [方法: タブ ページにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [方法: タブ ページを無効化する](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [方法: Windows フォーム TabControl のタブを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
