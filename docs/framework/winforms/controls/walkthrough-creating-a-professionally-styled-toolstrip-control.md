---
title: 'チュートリアル : プロフェッショナル スタイルの ToolStrip コントロールの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 2d2443f1f7153ed35aecbbb9d69c9e1421269e24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>チュートリアル : プロフェッショナル スタイルの ToolStrip コントロールの作成
アプリケーションを移すことができる<xref:System.Windows.Forms.ToolStrip>から派生した独自のクラスを記述して、プロフェッショナルな外観と動作を制御、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>型です。  
  
 このチュートリアルを使用する方法を示します<xref:System.Windows.Forms.ToolStrip>に似た複合コントロールを作成するコントロール、**ナビゲーション ウィンドウ**Microsoft® Outlook® によって提供されます。 次のタスクは、このチュートリアルで例を示します。  
  
-   Windows コントロール ライブラリ プロジェクトを作成します。  
  
-   StackView コントロールをデザインします。  
  
-   カスタム レンダラーを実装します。  
  
 完了したら、Microsoft Office® XP コントロールのプロフェッショナルな外観を持つカスタムのクライアントを再利用可能なコントロールがあります。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: プロフェッショナル スタイルの ToolStrip コントロールを作成](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。  
  
## <a name="creating-a-windows-control-library-project"></a>Windows コントロール ライブラリ プロジェクトを作成します。  
 最初の手順では、コントロール ライブラリ プロジェクトを作成します。  
  
#### <a name="to-create-the-control-library-project"></a>コントロール ライブラリ プロジェクトを作成するには  
  
1.  という名前の新しい Windows コントロール ライブラリ プロジェクトを作成する`StackViewLibrary`です。  
  
2.  **ソリューション エクスプ ローラー**、選択した言語に応じて"UserControl1.cs"または"UserControl1.vb"をという名前のソース ファイルを削除して、プロジェクトの既定のコントロールを削除します。  
  
     詳細については、次を参照してください。 [NIB: 方法:: 削除、削除、および項目の除外](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)です。  
  
3.  新しい<xref:System.Windows.Forms.UserControl>項目を**StackViewLibrary**プロジェクト。 新しいソース ファイルの基本の名前を付けます`StackView`です。  
  
## <a name="designing-the-stackview-control"></a>StackView コントロールのデザイン  
 `StackView`コントロールは、1 つの子による複合コントロール<xref:System.Windows.Forms.ToolStrip>コントロール。 複合コントロールの詳細については、次を参照してください。[カスタム コントロールの種類](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)です。  
  
#### <a name="to-design-the-stackview-control"></a>StackView コントロールを設計するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ToolStrip>コントロールをデザイン画面にします。  
  
2.  **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolStrip>次の表に従ってコントロールのプロパティです。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |名前|`stackStrip`|  
    |CanOverflow|`false`|  
    |ドッキング|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |フォント|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |[間隔]|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  Windows フォーム デザイナーでをクリックして、<xref:System.Windows.Forms.ToolStrip>コントロールの**追加**ボタンをクリックし、追加、<xref:System.Windows.Forms.ToolStripButton>を`stackStrip`コントロール。  
  
4.  **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolStripButton>次の表に従ってコントロールのプロパティです。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |名前|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Margin|`0, 0, 0, 0`|  
    |[間隔]|`3, 3, 3, 3`|  
    |テキスト|**メール**|  
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  複数の 3 つの手順 7.<xref:System.Windows.Forms.ToolStripButton>コントロール。  
  
     コントロールの名前を付けます`calendarStackButton`、 `contactsStackButton`、および`tasksStackButton`です。 値を設定、<xref:System.Windows.Forms.Control.Text%2A>プロパティを**カレンダー**、**連絡先**、および**タスク**、それぞれします。  
  
## <a name="handling-events"></a>イベントの処理  
 2 つのイベントは、重要な`StackView`コントロールが適切に動作します。 処理、<xref:System.Windows.Forms.UserControl.Load>コントロールを正しく配置するイベントです。 処理、<xref:System.Windows.Forms.ToolStripItem.Click>各イベント<xref:System.Windows.Forms.ToolStripButton>を与える、`StackView`のような状態の動作を制御、<xref:System.Windows.Forms.RadioButton>コントロール。  
  
#### <a name="to-handle-events"></a>イベントを処理するには  
  
1.  Windows フォーム デザイナーで、選択、`StackView`コントロール。  
  
2.  **プロパティ**ウィンドウで、をクリックして**イベント**です。  
  
3.  Load イベントをダブルクリックして、`StackView_Load`イベント ハンドラー。  
  
4.  `StackView_Load` イベント ハンドラーで、次のコードをコピーして貼り付けます。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  Windows フォーム デザイナーで、選択、`mailStackButton`コントロール。  
  
6.  **プロパティ**ウィンドウで、をクリックして**イベント**です。  
  
7.  Click イベントをダブルクリックします。  
  
     Windows フォーム デザイナーで生成する、`mailStackButton_Click`イベント ハンドラー。  
  
8.  名前を変更、`mailStackButton_Click`イベント ハンドラーを`stackButton_Click`です。  
  
     詳細については、次を参照してください。[する方法: 識別子 (Visual Basic) の名前を変更](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c)です。  
  
9. 次のコードを挿入、`stackButton_Click`イベント ハンドラー。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. Windows フォーム デザイナーで、選択、`calendarStackButton`コントロール。  
  
11. **プロパティ** ウィンドウの Click イベントを設定、`stackButton_Click`イベント ハンドラー。  
  
12. 手順 10 および 11 for、`contactsStackButton`と`tasksStackButton`コントロール。  
  
## <a name="defining-icons"></a>アイコンの定義  
 各`StackView`ボタンに関連付けられているアイコンがあります。 便宜上、各アイコンとして表されます、Base64 でエンコードされた文字列の前に逆シリアル化する、<xref:System.Drawing.Bitmap>から作成します。 実稼働環境でのリソースとしてビットマップ データを格納して、アイコン、Windows フォーム デザイナーに表示されます。 詳細については、次を参照してください。[する方法: Windows フォームの背景画像の追加](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff)です。  
  
#### <a name="to-define-icons"></a>アイコンを定義する  
  
1.  コード エディターに次のコードを挿入する、`StackView`クラス定義です。 このコードでのビットマップは初期化、<xref:System.Windows.Forms.ToolStripButton>アイコン。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  呼び出しを追加、`InitializeImages`メソッドで、`StackView`クラスのコンス トラクターです。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a>カスタム レンダラーを実装します。  
 要素の大部分をカスタマイズすることができます、`StackView`から派生するクラスを実装する、コントロール、<xref:System.Windows.Forms.ToolStripRenderer>クラスです。 この手順では、実装、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>グリップをカスタマイズしのグラデーションの背景を描画するクラス、<xref:System.Windows.Forms.ToolStripButton>コントロール。  
  
#### <a name="to-implement-a-custom-renderer"></a>カスタム レンダラーを実装するには  
  
1.  次のコードを挿入、`StackView`定義を制御します。  
  
     定義、`StackRenderer`クラスが優先、 <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>、 <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>、および<xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground>独自の外観を生成するメソッド。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  `StackView`コントロールのコンス トラクターの新しいインスタンスを作成、`StackRenderer`クラスし、このインスタンスに割り当てる、`stackStrip`コントロールの<xref:System.Windows.Forms.ToolStrip.Renderer%2A>プロパティです。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a>StackView コントロールのテスト  
 `StackView`から派生したコントロール、<xref:System.Windows.Forms.UserControl>クラスです。 そのため、コントロールをテストすることができます、 **UserControl Test Container**です。 詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
#### <a name="to-test-the-stackview-control"></a>StackView コントロールをテストするには  
  
1.  F5 キーを押して、プロジェクトをビルドし、開始、 **UserControl テスト コンテナー**です。  
  
2.  ボタンの上にポインターを移動、`StackView`を制御して、選択した状態の外観を表示するボタンをクリックします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Office XP コントロールのプロフェッショナルな外観とカスタムのクライアントを再利用可能なコントロールを作成しました。 使用することができます、<xref:System.Windows.Forms.ToolStrip>ファミリの他のさまざまな目的のコントロール。  
  
-   コントロールのショートカット メニューを作成する<xref:System.Windows.Forms.ContextMenuStrip>です。 詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)です。  
  
-   フォームを自動的に設定された標準のメニューを作成します。 詳細については、次を参照してください。[チュートリアル: 標準メニュー項目をフォームに](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)です。  
  
-   ドッキングとマルチ ドキュメント インターフェイス (MDI) フォームを作成する<xref:System.Windows.Forms.ToolStrip>コントロール。 詳細については、次を参照してください。[する方法: メニューのマージと ToolStrip コントロールを MDI フォームを作成](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [方法: フォームに標準メニュー項目を追加する](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
