---
title: "チュートリアル : 標準メニュー項目をフォームに用意する | Microsoft Docs"
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
  - "メニュー項目, 標準"
  - "StatusStrip コントロール [Windows フォーム]"
  - "ツール バー [Windows フォーム], チュートリアル"
  - "ToolStrip コントロール [Windows フォーム]"
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# チュートリアル : 標準メニュー項目をフォームに用意する
<xref:System.Windows.Forms.MenuStrip> コントロールを使って、標準メニューをフォームに用意できます。  
  
 このチュートリアルでは、<xref:System.Windows.Forms.MenuStrip> コントロールを使って標準メニューを作成する方法について説明します。  このフォームは、メニュー項目が選択されたときにもそれに応答する動作を実行します。  このチュートリアルでは、次のタスクについて説明します。  
  
-   Windows フォーム プロジェクトの作成  
  
-   標準メニューの作成  
  
-   <xref:System.Windows.Forms.StatusStrip> コントロールの作成  
  
-   メニュー項目選択の処理  
  
 タスクを完了すると、<xref:System.Windows.Forms.StatusStrip> コントロール内のメニュー項目選択を表示する標準メニューがあるフォームが完成します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : フォームに標準メニュー項目を追加する](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] がインストールされているコンピューターで、Windows フォーム アプリケーション プロジェクトを作成および実行するための十分なアクセス許可が付与されていること。  
  
## プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### プロジェクトを作成するには  
  
1.  StandardMenuForm という名前の Windows アプリケーション プロジェクトを作成します。  
  
     詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  Windows フォーム デザイナーで、フォームを選択します。  
  
## 標準メニューの作成  
 Windows フォーム デザイナーは、自動的に <xref:System.Windows.Forms.MenuStrip> コントロールに標準のメニュー項目を設定します。  
  
#### 標準メニューを作成するには  
  
1.  **ツールボックス**から、フォームに <xref:System.Windows.Forms.MenuStrip> コントロールをドラッグします。  
  
2.  <xref:System.Windows.Forms.MenuStrip> コントロールのスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックし、**\[標準項目の挿入\]** を選択します。  
  
     <xref:System.Windows.Forms.MenuStrip> コントロールに標準メニュー項目が設定されます。  
  
3.  **\[ファイル\]** メニュー項目をクリックして、既定のメニュー項目とアイコンを表示します。  
  
## StatusStrip コントロールの作成  
 <xref:System.Windows.Forms.StatusStrip> メソッドを使って、Windows フォーム アプリケーションのステータスを表示します。  現在の例では、ユーザーが選択したメニュー項目が <xref:System.Windows.Forms.StatusStrip> コントロールに表示されます。  
  
#### StatusStrip コントロールを作成するには  
  
1.  **ツールボックス**から、フォームに <xref:System.Windows.Forms.StatusStrip> コントロールをドラッグします。  
  
     <xref:System.Windows.Forms.StatusStrip> は、自動的にフォームの下部にドッキングされます。  
  
2.  <xref:System.Windows.Forms.StatusStrip> コントロールのドロップダウン リストをクリックし、**\[StatusLabel\]** を選択して <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールを <xref:System.Windows.Forms.StatusStrip> コントロールに追加します。  
  
## アイテム選択の処理  
 ユーザーがメニュー項目を選択したときに、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> イベントを処理してそれに応答します。  
  
#### 項目選択を処理するには  
  
1.  「標準メニューの作成」で作成した **\[ファイル\]** メニュー項目をクリックします。  
  
2.  **\[プロパティ\]** ウィンドウ ツール バーの **\[イベント\]** をクリックします。  
  
3.  <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> イベントをダブルクリックします。  
  
     Windows フォーム デザイナーが、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> イベントのイベント ハンドラーを生成します。  
  
4.  イベント ハンドラー内に次のコードを挿入します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  `UpdateStatus` ユーティリティ メソッドの定義をフォームに挿入します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## チェックポイント  
  
#### フォームをテストするには  
  
1.  F5 キーを押して、フォームをコンパイルおよび実行します。  
  
2.  **\[ファイル\]** メニュー項目をクリックしてメニューを開きます。  
  
3.  **\[ファイル\]** メニューで、次のいずれかの項目をクリックして選択します。  
  
     選択した項目が、<xref:System.Windows.Forms.StatusStrip> コントロールに表示されます。  
  
## 次の手順  
 このチュートリアルでは、標準メニューを備えたフォームを作成しました。  <xref:System.Windows.Forms.ToolStrip> 系コントロールの用途は、他にもたくさんあります。  
  
-   <xref:System.Windows.Forms.ContextMenuStrip> を使って、コントロールにショートカット メニューを作成します。  詳細については、「[ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.ToolStrip> コントロールがドッキングされている、複数のマルチ ドキュメント インターフェイス \(MDI\) フォームを作成します。  詳細については、「[チュートリアル : メニューのマージと ToolStrip コントロールのある MDI フォームを作成する](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.ToolStrip> コントロールにプロフェッショナルな外観を与えます。  詳細については、「[方法 : アプリケーションの ToolStrip レンダラーを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)