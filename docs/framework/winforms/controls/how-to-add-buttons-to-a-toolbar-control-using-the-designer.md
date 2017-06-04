---
title: "方法 : デザイナーを使って ToolBar コントロールにボタンを追加する | Microsoft Docs"
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
  - "例 [Windows フォーム], ツール バー"
  - "ToolBar コントロール [Windows フォーム], 追加 (ボタンを)"
  - "ToolBar コントロール [Windows フォーム], 追加 (ドロップダウン メニューを)"
  - "ToolBar コントロール [Windows フォーム], 追加 (区切り記号を)"
  - "ツール バー [Windows フォーム], 追加 (ボタンを)"
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : デザイナーを使って ToolBar コントロールにボタンを追加する
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 <xref:System.Windows.Forms.ToolBar> コントロールの重要な要素は、このコントロールに追加するボタンです。  追加するボタンは、メニュー コマンドへ手軽にアクセスするために使用できます。また、アプリケーションのユーザー インターフェイスの別の部分にボタンを配置することにより、メニュー構造では利用できないコマンドをユーザーに提供することもできます。  
  
 次の手順では、<xref:System.Windows.Forms.ToolBar> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時にボタンを追加するには  
  
1.  <xref:System.Windows.Forms.ToolBar> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.ToolBar.Buttons%2A> プロパティをクリックして選択し、**省略記号** \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックして **ToolBarButton コレクション エディター**を表示します。  
  
3.  <xref:System.Windows.Forms.ToolBar> コントロールにボタンを追加するには **\[追加\]** をクリックし、削除するには **\[削除\]** をクリックします。  
  
4.  エディターの右側のペインに表示される **\[プロパティ\]** ウィンドウで、各ボタンのプロパティを設定します。  考慮する必要がある重要なプロパティを次の表に示します。  
  
    |プロパティ|Description|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|ドロップダウン ツール バー ボタンに表示されるメニューを設定します。  ツール バー ボタンの <xref:System.Windows.Forms.ToolBarButton.Style%2A> プロパティが <xref:System.Windows.Forms.ToolBarButtonStyle> に設定されている必要があります。  このプロパティは、<xref:System.Windows.Forms.ContextMenu> クラスのインスタンスを参照として受け取ります。|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|切り替え形式のツール バー ボタンを部分的に押されている状態にするかどうかを設定します。  ツール バー ボタンの <xref:System.Windows.Forms.ToolBarButton.Style%2A> プロパティが <xref:System.Windows.Forms.ToolBarButtonStyle> に設定されている必要があります。|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|切り替え形式のツール バー ボタンを押されている状態にするかどうかを設定します。  ツール バー ボタンの <xref:System.Windows.Forms.ToolBarButton.Style%2A> プロパティが <xref:System.Windows.Forms.ToolBarButtonStyle> または <xref:System.Windows.Forms.ToolBarButtonStyle> に設定されている必要があります。|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|ツール バー ボタンのスタイルを設定します   <xref:System.Windows.Forms.ToolBarButtonStyle> 列挙値のいずれかの値にする必要があります。|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|ボタンによって表示される文字列です。|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|ボタンのツールヒントとして表示されるテキストです。|  
  
5.  **\[OK\]** をクリックしてダイアログ ボックスを閉じ、指定したパネルを作成します。  
  
## 参照  
 <xref:System.Windows.Forms.ToolBar>   
 [方法 : ツール バー ボタンのアイコンを定義する](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [方法 : ツール バー ボタンのメニュー イベントをトリガーする](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [ToolBar コントロールの概要](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)   
 [ToolBar コントロール](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)