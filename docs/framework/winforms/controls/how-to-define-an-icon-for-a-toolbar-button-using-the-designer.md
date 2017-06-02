---
title: "方法 :デザイナーを使って ToolBar ボタンのアイコンを定義する | Microsoft Docs"
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
  - "ボタン [Windows フォーム], イメージ"
  - "例 [Windows フォーム], ツール バー"
  - "アイコン [Windows フォーム], ツール バー ボタン"
  - "イメージ [Windows フォーム], ツール バー ボタン"
  - "ToolBar コントロール [Windows フォーム], 追加 (ボタンにアイコンを)"
  - "ツール バー [Windows フォーム], 追加 (ボタンにアイコンを)"
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 :デザイナーを使って ToolBar ボタンのアイコンを定義する
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 <xref:System.Windows.Forms.ToolBar> のボタンには、ユーザーが簡単に識別できるようにアイコンを表示することができます。  そうするには、イメージを <xref:System.Windows.Forms.ImageList> コンポーネントに追加し、これを <xref:System.Windows.Forms.ToolBar> コントロールに関連付けます。  
  
 次の手順では、<xref:System.Windows.Forms.ToolBar> コントロールと <xref:System.Windows.Forms.ImageList> コンポーネントが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時にツール バー ボタンのアイコンを設定するには  
  
1.  イメージを <xref:System.Windows.Forms.ImageList> コンポーネントに追加します。  詳細については、「[方法 : デザイナーを使って ImageList イメージを追加または削除する](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md)」を参照してください。  
  
2.  フォームで <xref:System.Windows.Forms.ToolBar> コントロールを選択します。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.ToolBar> コントロールの <xref:System.Windows.Forms.ToolBar.ImageList%2A>プロパティの値を <xref:System.Windows.Forms.ImageList> に設定します。  
  
4.  <xref:System.Windows.Forms.ToolBar> コントロールの <xref:System.Windows.Forms.ToolBar.Buttons%2A> プロパティをクリックして選択し、省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして **ToolBarButton コレクション エディター**を開きます。  
  
5.  **\[追加\]** をクリックして <xref:System.Windows.Forms.ToolBar> コントロールにボタンを追加します。  
  
6.  **ToolBarButton コレクション エディター**の右側のペインに表示される **\[プロパティ\]** ウィンドウで、各ツール バー ボタンの <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> プロパティに、一覧に表示されたいずれかの値を設定します。一覧の値は、<xref:System.Windows.Forms.ImageList> コンポーネントに追加したイメージから取得されます。  
  
## 参照  
 <xref:System.Windows.Forms.ToolBar>   
 [方法 : ツール バー ボタンのメニュー イベントをトリガーする](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [ToolBar コントロール](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)