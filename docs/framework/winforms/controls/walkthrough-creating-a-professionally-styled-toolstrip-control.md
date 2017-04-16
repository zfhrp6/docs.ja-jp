---
title: "チュートリアル : プロフェッショナル スタイルの ToolStrip コントロールの作成 | Microsoft Docs"
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
  - "ツール バー [Windows フォーム], チュートリアル"
  - "ToolStrip コントロール [Windows フォーム], 作成 (プロフェッショナル スタイルのコントロールを)"
  - "ToolStripProfessionalRenderer クラス [Windows フォーム]"
  - "ToolStripRenderer クラス [Windows フォーム]"
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# チュートリアル : プロフェッショナル スタイルの ToolStrip コントロールの作成
<xref:System.Windows.Forms.ToolStripProfessionalRenderer> 型から派生する独自のクラスを記述することで、アプリケーションの <xref:System.Windows.Forms.ToolStrip> コントロールにプロフェッショナルな外観と動作を与えることができます。  
  
 このチュートリアルでは、<xref:System.Windows.Forms.ToolStrip> コントロールを使用して、Microsoft® Outlook® の**ナビゲーション ペイン**に似た複合コントロールを作成する方法について説明します。  このチュートリアルでは、次のタスクについて説明します。  
  
-   新しい Windows コントロール ライブラリ プロジェクトを作成します。  
  
-   StackView コントロールをデザインします。  
  
-   カスタム レンダラーを割り当てます。  
  
 これらのタスクを終了すると、Microsoft Office® XP コントロールのプロフェッショナルな外観を備えた、再利用できるカスタム クライアント コントロールが作成されます。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : プロフェッショナル スタイルの ToolStrip コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] がインストールされているコンピューターで、Windows フォーム アプリケーション プロジェクトを作成および実行するための十分なアクセス許可が付与されていること。  
  
## コントロール ライブラリ プロジェクトの作成  
 最初に、コントロール ライブラリ プロジェクトを作成します。  
  
#### コントロール ライブラリ プロジェクトを作成するには  
  
1.  `StackViewLibrary` という新しい Windows コントロール ライブラリ プロジェクトを作成します。  
  
2.  **ソリューション エクスプローラー**で、選択した言語に応じて "UserControl1.cs" または "UserControl1.vb" という名前のソース ファイルを削除して、プロジェクトの既定のコントロールを削除します。  
  
     詳細については、「[NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/ja-jp/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)」を参照してください。  
  
3.  新しい <xref:System.Windows.Forms.UserControl> アイテムを **StackViewLibrary** プロジェクトに追加します。  新しいソース ファイルに、"`StackView`" という基本名を付けます。  
  
## StackView コントロールのデザイン  
 `StackView` コントロールは、1 つの子コントロール <xref:System.Windows.Forms.ToolStrip> を含む複合コントロールです。  複合コントロールの詳細については、「[さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)」を参照してください。  
  
#### StackView コントロールをデザインするには  
  
1.  **ツールボックス**からデザイン サーフェイスに <xref:System.Windows.Forms.ToolStrip> コントロールを追加します。  
  
2.  **プロパティ** ウィンドウで、次の表に従って <xref:System.Windows.Forms.ToolStrip> コントロールのプロパティを設定します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |名前|`stackStrip`|  
    |CanOverflow|`false`|  
    |Dock|<xref:System.Windows.Forms.DockStyle>|  
    |フォント|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle>|  
    |Padding|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode>|  
  
3.  Windows フォーム デザイナーで <xref:System.Windows.Forms.ToolStrip> コントロールの **\[追加\]** ボタンをクリックし、<xref:System.Windows.Forms.ToolStripButton> を `stackStrip` コントロールへ追加します。  
  
4.  **プロパティ** ウィンドウで、次の表に従って <xref:System.Windows.Forms.ToolStripButton> コントロールのプロパティを設定します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |名前|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Margin|`0, 0, 0, 0`|  
    |Padding|`3, 3, 3, 3`|  
    |テキスト|Mail|  
    |TextAlign|<xref:System.Drawing.ContentAlignment>|  
  
5.  残りの 3 つの <xref:System.Windows.Forms.ToolStripButton> コントロールについても手順 7. を繰り返します。  
  
     `calendarStackButton` コントロール、`contactsStackButton` コントロール、および `tasksStackButton` コントロールに名前を付けます。  <xref:System.Windows.Forms.Control.Text%2A> プロパティの値を、それぞれ Calendar、Contacts、および Tasks に設定します。  
  
## イベントの処理  
 `StackView` コントロールが適切に動作するようにするには、2 つのイベントが重要です。  コントロールの位置を適切に指定するには <xref:System.Windows.Forms.UserControl.Load> イベントを処理します。  `StackView` コントロールの状態を <xref:System.Windows.Forms.RadioButton> コントロールと似た動作にするには、<xref:System.Windows.Forms.ToolStripButton> ごとに <xref:System.Windows.Forms.ToolStripItem.Click> イベントを処理します。  
  
#### イベントを処理するには  
  
1.  Windows フォーム デザイナーで、`StackView` コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウ ツール バーの **\[イベント\]** をクリックします。  
  
3.  Load イベントをダブルクリックして、`StackView_Load` イベント ハンドラーを生成します。  
  
4.  次のコードをコピーし、`StackView_Load` イベント ハンドラーに貼り付けます。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  Windows フォーム デザイナーで、`mailStackButton` コントロールを選択します。  
  
6.  **\[プロパティ\]** ウィンドウ ツール バーの **\[イベント\]** をクリックします。  
  
7.  \[Click\] イベントをダブルクリックします。  
  
     Windows フォーム デザイナーで `mailStackButton_Click` イベント ハンドラーが生成されます。  
  
8.  `mailStackButton_Click` イベント ハンドラーの名前を `stackButton_Click` に変更します。  
  
     詳細については、「[How to: Rename an Identifier \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/e5a5edf8-3dba-4119-81f4-fc2aba180e0c)」を参照してください。  
  
9. `stackButton_Click` イベント ハンドラー内に次のコードを挿入します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. Windows フォーム デザイナーで、`calendarStackButton` コントロールを選択します。  
  
11. **\[プロパティ\]** ウィンドウで、Click イベントを `stackButton_Click` イベント ハンドラーに設定します。  
  
12. `contactsStackButton` コントロールと `tasksStackButton` コントロールについて、手順 10. と手順 11. を繰り返します。  
  
## アイコンの定義  
 各 `StackView` にはアイコンが関連付けられています。  わかりやすいように、各アイコンは Base64 でエンコードされた文字列で表されます。この文字列は、<xref:System.Drawing.Bitmap> を作成する前に逆シリアル化されます。  稼動環境では、ビットマップ データをリソースとして格納すると、Windows フォーム デザイナーにアイコンが表示されます。  詳細については、「[How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/ja-jp/7a509ba2-055c-4ae6-b88a-54625c6d9aff)」を参照してください。  
  
#### アイコンを定義するには  
  
1.  コード エディターで、次のコードを `StackView` クラス定義に追加します。  このコードでは、<xref:System.Windows.Forms.ToolStripButton> アイコンのビットマップを初期化します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  `StackView` クラス コンストラクターに `InitializeImages` メソッドの呼び出しを追加します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## カスタム レンダラーの実装  
 <xref:System.Windows.Forms.ToolStripRenderer> クラスから派生するクラスを実装することによって、`StackView` コントロールでは、ほとんどの要素をカスタマイズできます。  この手順では、<xref:System.Windows.Forms.ToolStripButton> コントロールについて、グリップをカスタマイズし、グラデーションの背景を描画する <xref:System.Windows.Forms.ToolStripProfessionalRenderer> クラスを実装します。  
  
#### カスタム レンダラーを実装するには  
  
1.  `StackView` コントロール定義内に次のコードを挿入します。  
  
     これは `StackRenderer` クラスの定義です。この定義は、<xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>、<xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>、および <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> の各メソッドをオーバーライドし、カスタムの外観を作成します。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  `StackView` コントロールのコンストラクターで、`StackRenderer` クラスの新しいインスタンスを作成し、そのインスタンスを `stackStrip` コントロールの <xref:System.Windows.Forms.ToolStrip.Renderer%2A> プロパティに割り当てます。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## StackView コントロールのテスト  
 `StackView` コントロールは <xref:System.Windows.Forms.UserControl> クラスから派生します。  そのため、このコントロールは**UserControl Test Container**でテストできます。  詳細については、「[方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
#### StackView コントロールをテストするには  
  
1.  F5 キーを押してプロジェクトをビルドし、**UserControl Test Container**を起動します。  
  
2.  `StackView` コントロールのボタンにマウス ポインターを移動し、ボタンをクリックすると、選択した状態の外観が表示されます。  
  
## 次の手順  
 このチュートリアルでは、Office XP コントロールのプロフェッショナルな外観を備えた、再利用できるカスタム コントロールを作成しました。  <xref:System.Windows.Forms.ToolStrip> 系コントロールの用途は、他にもたくさんあります。  
  
-   <xref:System.Windows.Forms.ContextMenuStrip> を使って、コントロールにショートカット メニューを作成します。  詳細については、「[ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)」を参照してください。  
  
-   標準メニューに自動的に項目が設定されるフォームを作成します。  詳細については、「[チュートリアル : 標準メニュー項目をフォームに用意する](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.ToolStrip> コントロールがドッキングされている、複数のマルチ ドキュメント インターフェイス \(MDI\) フォームを作成します。  詳細については、「[方法 : メニューのマージと ToolStrip コントロールを使用して MDI フォームを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [方法 : フォームに標準メニュー項目を追加する](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)