---
title: "チュートリアル : メニューのマージと ToolStrip コントロールのある MDI フォームを作成する | Microsoft Docs"
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
  - "MDI フォーム"
  - "MDI フォーム, 作成"
  - "MDI フォーム, チュートリアル"
  - "MDI, 作成 (フォームを)"
  - "マルチ ドキュメント インターフェイス (MDI) フォーム"
  - "ツール バー [Windows フォーム]"
  - "ToolStrip コントロール [Windows フォーム]"
  - "ToolStripPanel コントロール [Windows フォーム]"
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# チュートリアル : メニューのマージと ToolStrip コントロールのある MDI フォームを作成する
<xref:System.Windows.Forms?displayProperty=fullName> 名前空間は、複数のマルチ ドキュメント インターフェイス \(MDI\) アプリケーションをサポートし、<xref:System.Windows.Forms.MenuStrip> コントロールは、メニューのマージをサポートします。  MDI フォームでは、<xref:System.Windows.Forms.ToolStrip> コントロールも使用できます。  
  
 このチュートリアルでは、MDI フォームで <xref:System.Windows.Forms.ToolStripPanel> コントロールを使用する方法について説明します。  このフォームには、メニューを子メニューとマージする機能もあります。  このチュートリアルでは、次のタスクについて説明します。  
  
-   Windows フォーム プロジェクトの作成  
  
-   フォームのメイン メニューを作成   \(実際のメニュー名は異なります\)  
  
-   **ツールボックス**への <xref:System.Windows.Forms.ToolStripPanel> コントロールの追加  
  
-   子フォームの作成  
  
-   z オーダーによる <xref:System.Windows.Forms.ToolStripPanel> コントロールの並べ替え  
  
 すべてのタスクを完了すると、メニューのマージおよび移動可能な <xref:System.Windows.Forms.ToolStrip> コントロールをサポートする MDI フォームが完成します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : メニューのマージと ToolStrip コントロールを使用して MDI フォームを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] がインストールされているコンピューターで、Windows フォーム アプリケーション プロジェクトを作成および実行するための十分なアクセス許可が付与されていること。  
  
## プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### プロジェクトを作成するには  
  
1.  MdiForm という名前の Windows アプリケーション プロジェクトを作成します。  
  
     詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  Windows フォーム デザイナーで、フォームを選択します。  
  
3.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.Form.IsMdiContainer%2A> の値を `true` に設定します。  
  
## メイン メニューの作成  
 親 MDI フォームにはメイン メニューがあります。  メイン メニューには **\[ウィンドウ\]** というメニュー項目が 1 つあります。  **\[ウィンドウ\]** メニュー項目を使用して、子フォームを作成できます。  子フォームのメニュー項目は、メイン メニューにマージされます。  
  
#### メイン メニューを作成するには  
  
1.  **ツールボックス**から、フォームに <xref:System.Windows.Forms.MenuStrip> コントロールをドラッグします。  
  
2.  <xref:System.Windows.Forms.ToolStripMenuItem> を <xref:System.Windows.Forms.MenuStrip> コントロールに追加し、\[ウィンドウ\] と名付けます。  
  
3.  <xref:System.Windows.Forms.MenuStrip> コントロールを選択します。  
  
4.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> プロパティの値を `ToolStripMenuItem1` に設定します。  
  
5.  サブ項目を **\[ウィンドウ\]** メニューに追加し、\[新規作成\] と名付けます。  
  
6.  \[プロパティ\] ウィンドウの **\[イベント\]** をクリックします。  
  
7.  <xref:System.Windows.Forms.ToolStripItem.Click> イベントをダブルクリックします。  
  
     Windows フォーム デザイナーが、<xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを生成します。  
  
8.  イベント ハンドラー内に次のコードを挿入します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## ツールボックスへの ToolStripPanel コントロールの追加  
 MDI フォームで <xref:System.Windows.Forms.MenuStrip> コントロールを使用するときは、<xref:System.Windows.Forms.ToolStripPanel> コントロールが必要です。  MDI フォームを Windows フォーム デザイナー内でビルドするために、<xref:System.Windows.Forms.ToolStripPanel> コントロールを**ツールボックス**に追加する必要があります。  
  
#### ToolStripPanel コントロールをツールボックスに追加するには  
  
1.  **ツールボックス**を開き、**\[すべての Windows フォーム\]** タブをクリックすると、使用できる Windows フォーム コントロールが表示されます。  
  
2.  コントロールを右クリックしてショートカット メニューを開き、**\[アイテムの選択\]** をクリックします。  
  
3.  **\[ツールボックス アイテムの選択\]** ダイアログ ボックスで、**\[ToolStripPanel\]** が表示されるまで **\[名前\]** 列をスクロールします。  
  
4.  **\[ToolStripPanel\]** チェック ボックスをオンにし、**\[OK\]** をクリックします。  
  
     <xref:System.Windows.Forms.ToolStripPanel> コントロールが**ツールボックス**に表示されます。  
  
## 子フォームの作成  
 この手順では、別個の <xref:System.Windows.Forms.MenuStrip> コントロールを持つ独立した子フォーム クラスを定義します。  このフォームのメニュー項目は、親フォームのメニュー項目にマージされます。  
  
#### 子フォームを定義するには  
  
1.  `ChildForm` という名前の新規フォームをプロジェクトに追加します。  
  
     詳細については、「[How to: Add Windows Forms to a Project](http://msdn.microsoft.com/ja-jp/3d7bb25f-fd90-47cf-9378-fa0d764686c1)」を参照してください。  
  
2.  **ツールボックス**から、子フォームに <xref:System.Windows.Forms.MenuStrip> コントロールをドラッグします。  
  
3.  <xref:System.Windows.Forms.MenuStrip> コントロールのスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックし、**\[項目の編集\]** を選択します。  
  
4.  **\[項目コレクション エディター\]** ダイアログ ボックスで、ChildMenuItem という名前の新しい <xref:System.Windows.Forms.ToolStripMenuItem> を子メニューに追加します。  
  
     詳細については、「[ToolStrip Items Collection Editor](http://msdn.microsoft.com/ja-jp/e681f3ab-94ba-4b2b-ac64-1dfad46caa25)」を参照してください。  
  
## フォームのテスト  
  
#### フォームをテストするには  
  
1.  F5 キーを押して、フォームをコンパイルおよび実行します。  
  
2.  **\[ウィンドウ\]** メニュー項目をクリックしてメニューを開き、**\[新規作成\]** をクリックします。  
  
     新規の子フォームが、フォームの MDI クライアント領域に作成されます。  子フォームのメニューが、メイン メニューにマージされます。  
  
3.  子フォームを閉じます。  
  
     子フォームのメニューは、メイン メニューから削除されます。  
  
4.  **\[新規作成\]** を数回クリックします。  
  
     <xref:System.Windows.Forms.MenuStrip> コントロールの <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> プロパティが割り当てられるため、複数の子フォームが自動的に **\[ウィンドウ\]** メニュー項目の下に表示されます。  
  
## ToolStrip サポートの追加  
 この手順では、4 つの <xref:System.Windows.Forms.ToolStrip> コントロールを MDI 親フォームに追加します。  各 <xref:System.Windows.Forms.ToolStrip> コントロールは <xref:System.Windows.Forms.ToolStripPanel> コントロール内に追加され、このコントロールがフォームの端にドッキングされます。  
  
#### ToolStrip コントロールを MDI 親フォームに追加するには  
  
1.  **ツールボックス**から、フォームに <xref:System.Windows.Forms.ToolStripPanel> コントロールをドラッグします。  
  
2.  <xref:System.Windows.Forms.ToolStripPanel> コントロールを選択した状態で、**ツールボックス**内の <xref:System.Windows.Forms.ToolStrip> コントロールをダブルクリックします。  
  
     <xref:System.Windows.Forms.ToolStrip> コントロールが、<xref:System.Windows.Forms.ToolStripPanel> コントロール内に作成されます。  
  
3.  <xref:System.Windows.Forms.ToolStripPanel> コントロールを選択します。  
  
4.  \[プロパティ\] ウィンドウで、コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に変更します。  
  
     <xref:System.Windows.Forms.ToolStripPanel> コントロールがフォームの左側、メイン メニューの下にドッキングされます。  MDI クライアント領域は、<xref:System.Windows.Forms.ToolStripPanel> コントロールが収まるサイズに変更されます。  
  
5.  手順 1. ～ 4. を繰り返します。  
  
     新しい <xref:System.Windows.Forms.ToolStripPanel> コントロールは、フォームの上部にドッキングされます。  
  
     <xref:System.Windows.Forms.ToolStripPanel> コントロールはメイン メニューの下にドッキングされますが、今回は最初の <xref:System.Windows.Forms.ToolStripPanel> コントロールの右側に配置されます。  この手順は、<xref:System.Windows.Forms.ToolStripPanel> コントロールを適切に配置する際の z オーダーの役割をよく示しています。  
  
6.  さらに 2 つの <xref:System.Windows.Forms.ToolStripPanel> コントロールについて、手順 1. ～ 4. を繰り返します。  
  
     新規の <xref:System.Windows.Forms.ToolStripPanel> コントロールは、フォームの右側の下部にドッキングされます。  
  
## z オーダーによる ToolStripPanel コントロールの並べ替え  
 MDI フォームにドッキングされる <xref:System.Windows.Forms.ToolStripPanel> コントロールの位置は、z オーダーにおけるそのコントロールの位置によって決定されます。  コントロールの z オーダーは、\[ドキュメント アウトライン\] ウィンドウで簡単に設定できます。  
  
#### z オーダーに従って ToolStripPanel コントロールを並べ替えるには  
  
1.  **\[表示\]** メニューの **\[その他のウィンドウ\]** をクリックし、**\[ドキュメント アウトライン\]** をクリックします。  
  
     前の手順で使用した <xref:System.Windows.Forms.ToolStripPanel> コントロールの順序は、標準の順序ではありません。  これは、z オーダーが正しくないためです。  \[ドキュメント アウトライン\] ウィンドウを使って、コントロールの z オーダーを変更します。  
  
2.  \[ドキュメント アウトライン\] ウィンドウで、**\[ToolStripPanel4\]** を選択します。  
  
3.  **\[ToolStripPanel4\]** が一覧の最後に移動するまで、下向きの矢印ボタンを繰り返しクリックします。  
  
     **\[ToolStripPanel4\]** コントロールは、フォームの下部に、他のコントロールの下になる配置でドッキングされます。  
  
4.  **\[ToolStripPanel2\]** を選択します。  
  
5.  下向き矢印ボタンを 1 度クリックして、リストで 3 番目のコントロールの位置を指定します。  
  
     **\[ToolStripPanel2\]** コントロールは、フォームの上部に、メイン メニューの下で他のコントロールの上になる配置でドッキングされます。  
  
6.  さまざまなコントロールを **\[ドキュメント アウトライン\]** ウィンドウで選択し、z オーダーの異なる位置に移動します。  z オーダーに従って、ドッキングされたコントロールの配置が変わることを確認してください。  Ctrl キーを押しながら Z キーを押すか、**\[編集\]** メニューの **\[元に戻す\]** をクリックすると、変更は元に戻ります。  
  
## チェックポイント  
  
#### フォームをテストするには  
  
1.  F5 キーを押して、フォームをコンパイルおよび実行します。  
  
2.  <xref:System.Windows.Forms.ToolStrip> コントロールのグリップをクリックし、コントロールをフォームの異なる位置へドラッグします。  
  
     <xref:System.Windows.Forms.ToolStrip> コントロールをある <xref:System.Windows.Forms.ToolStripPanel> コントロールからドラッグして別のコントロールへ移動できます。  
  
## 次の手順  
 このチュートリアルでは、<xref:System.Windows.Forms.ToolStrip> コントロールとメニューのマージ機能を備えた MDI 親フォームを作成しました。  <xref:System.Windows.Forms.ToolStrip> 系コントロールの用途は、他にもたくさんあります。  
  
-   <xref:System.Windows.Forms.ContextMenuStrip> を使って、コントロールにショートカット メニューを作成します。  詳細については、「[ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)」を参照してください。  
  
-   標準メニューに自動的に項目が設定されるフォームを作成します。  詳細については、「[チュートリアル : 標準メニュー項目をフォームに用意する](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.ToolStrip> コントロールにプロフェッショナルな外観を与えます。  詳細については、「[方法 : アプリケーションの ToolStrip レンダラーを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [方法 : MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [方法 : MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [方法 : MDI ドロップダウン メニューに MenuStrip を挿入する](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)   
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)