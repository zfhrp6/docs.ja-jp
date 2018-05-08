---
title: '方法 : デザイナーを使って ToolBar コントロールにボタンを追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: e90732329a0d78421d09da1c405ed93d5cb82f23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>方法 : デザイナーを使って ToolBar コントロールにボタンを追加する
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 不可欠な<xref:System.Windows.Forms.ToolBar>コントロールは、ボタンを追加します。 メニュー コマンドに簡単にアクセスを提供する使用できるか、または、コマンド メニュー構造では使用できないことを公開するアプリケーションのユーザー インターフェイスの別の領域に配置することができます。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.ToolBar>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-buttons-at-design-time"></a>デザイン時にボタンを追加するには  
  
1.  <xref:System.Windows.Forms.ToolBar> コントロールを選択します。  
  
2.  **プロパティ**ウィンドウで、をクリックして、<xref:System.Windows.Forms.ToolBar.Buttons%2A>プロパティを選択し、クリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を開く ボタン、 **ToolBarButton コレクション エディター**です。  
  
3.  使用して、**追加**と**削除**ボタンを追加および削除からボタン、<xref:System.Windows.Forms.ToolBar>コントロール。  
  
4.  各ボタンのプロパティを構成、**プロパティ**エディターの右側のペインに表示されるウィンドウ。 次の表は、考慮すべきいくつかの重要なプロパティを示しています。  
  
    |プロパティ|説明|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|ツールバーのドロップダウンに表示されるメニューを設定します。 ツール バー ボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>プロパティに設定する必要があります<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>です。 このプロパティは、のインスタンスを受け取り、<xref:System.Windows.Forms.ContextMenu>クラスとして参照します。|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|スタイルの切り替えツールバーのボタンが部分的にプッシュされたかどうかを設定します。 ツール バー ボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>プロパティに設定する必要があります<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>です。|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|スタイルの切り替えツールバーのボタンが押されている状態は現在あるかどうかを設定します。 ツール バー ボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>プロパティに設定する必要があります<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>または<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>です。|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|ツール バー ボタンのスタイルを設定します。 内の値のいずれかを指定する必要があります、<xref:System.Windows.Forms.ToolBarButtonStyle>列挙します。|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|ボタンによって表示される文字列。|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|ボタンのツールヒントとして表示されるテキストです。|  
  
5.  をクリックして**OK**をダイアログ ボックスを閉じるし、指定したパネルを作成します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolBar>  
 [方法: ツール バー ボタンのアイコンを定義する](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [方法: ツール バー ボタンのメニュー イベントをトリガーする](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar コントロールの概要](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [ToolBar コントロール](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
