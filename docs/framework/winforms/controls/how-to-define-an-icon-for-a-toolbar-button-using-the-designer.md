---
title: "方法 :デザイナーを使って ToolBar ボタンのアイコンを定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d8bdad3aa17c964871c0d35f6e33b8098f2c649
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>方法 :デザイナーを使って ToolBar ボタンのアイコンを定義する
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 <xref:System.Windows.Forms.ToolBar>ボタンは、ユーザーがそれらに含まれるを識別しやすくのアイコンを表示できます。 これに画像を追加することによって実現、<xref:System.Windows.Forms.ImageList>コンポーネントと関連付けることで、<xref:System.Windows.Forms.ToolBar>コントロール。  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.ToolBar>コントロールと<xref:System.Windows.Forms.ImageList>コンポーネントです。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>デザイン時ツール バー ボタンのアイコンを設定するには  
  
1.  イメージを追加、<xref:System.Windows.Forms.ImageList>コンポーネントです。 詳細については、次を参照してください。[する方法: デザイナーを使って ImageList イメージを追加または](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md)です。  
  
2.  選択、<xref:System.Windows.Forms.ToolBar>フォーム上のコントロールです。  
  
3.  **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolBar>コントロールの<xref:System.Windows.Forms.ToolBar.ImageList%2A>プロパティを<xref:System.Windows.Forms.ImageList>コンポーネントです。  
  
4.  クリックして、<xref:System.Windows.Forms.ToolBar>コントロールの<xref:System.Windows.Forms.ToolBar.Buttons%2A>プロパティを選択し、省略記号ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を開くには、ボタン**ToolBarButton コレクション エディター**です。  
  
5.  使用して、**追加**ボタンを追加するにはボタン、<xref:System.Windows.Forms.ToolBar>コントロール。  
  
6.  **プロパティ**の右側のペインに表示されるウィンドウ、 **ToolBarButton コレクション エディター**、設定、<xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A>各ツールバーのボタン、リスト内の値のいずれかのプロパティを追加した画像の描画、<xref:System.Windows.Forms.ImageList>コンポーネントです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolBar>  
 [方法: ツール バー ボタンのメニュー イベントをトリガーする](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar コントロール](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
