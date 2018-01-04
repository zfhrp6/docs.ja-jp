---
title: "チュートリアル : デザイナーを使用した、ListView コントロールと TreeView コントロールを含むエクスプローラー スタイルのインターフェイスの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 200c5bbb5a162c1e585fc35f9c8cb3f63eb0368e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>チュートリアル : デザイナーを使用した、ListView コントロールと TreeView コントロールを含むエクスプローラー スタイルのインターフェイスの作成
Visual Studio の利点の 1 つは、時間の短い形式でプロ並みの Windows フォーム アプリケーションを作成する権限です。 一般的なシナリオは、ユーザー インターフェイス (UI) を作成するとは<xref:System.Windows.Forms.ListView>と<xref:System.Windows.Forms.TreeView>Windows エクスプ ローラーの機能の Windows オペレーティング システムのようなコントロールです。 Windows エクスプ ローラーでは、ユーザーのコンピューター上のファイルとフォルダーの階層構造を表示します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>ListView コントロールと TreeView コントロールを含むフォームを作成するには  
  
1.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、次の操作します。  
  
    1.  カテゴリで選択するか**Visual Basic**または**Visual c#**です。  
  
    2.  テンプレートの一覧で選択**Windows フォーム アプリケーション**です。  
  
3.  **[OK]**をクリックします。 新しい Windows フォーム プロジェクトが作成されます。  
  
4.  追加、<xref:System.Windows.Forms.SplitContainer>コントロールをフォームと設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>です。  
  
5.  追加、<xref:System.Windows.Forms.ImageList>という`imageList1`フォームと 2 つのイメージを追加する [プロパティ] ウィンドウを使用する: フォルダー イメージとその順序で、ドキュメント イメージ。  
  
6.  追加、<xref:System.Windows.Forms.TreeView>という名前のコントロール`treeview1`フォームの左側に配置し、<xref:System.Windows.Forms.SplitContainer>コントロール。 [プロパティ] ウィンドウで`treeView1`次の操作します。  
  
    1.  <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill> に設定します。  
  
    2.  <xref:System.Windows.Forms.TreeView.ImageList%2A> プロパティを `imagelist1.` に設定します。  
  
7.  追加、<xref:System.Windows.Forms.ListView>という名前のコントロール`listView1`フォームの右側に配置し、<xref:System.Windows.Forms.SplitContainer>コントロール。 [プロパティ] ウィンドウで`listview1`次の操作します。  
  
    1.  <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill> に設定します。  
  
    2.  <xref:System.Windows.Forms.ListView.View%2A> プロパティを <xref:System.Windows.Forms.View.Details> に設定します。  
  
    3.  省略記号ボタンをクリックして ColumnHeader コレクション エディターを開きます (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) で、<xref:System.Windows.Forms.ListView.Columns%2A>プロパティ**です。** 3 つの列を追加し、設定、<xref:System.Windows.Forms.ColumnHeader.Text%2A>プロパティを`Name`、 `Type`、および`Last Modified`、それぞれします。 **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
    4.  <xref:System.Windows.Forms.ListView.SmallImageList%2A> プロパティを `imageList1.` に設定します。  
  
8.  データを読み込むコードを実装する、<xref:System.Windows.Forms.TreeView>ノードとサブノードを使用します。 `Form1` クラスに次のコードを追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. 上記のコードでは、名前空間を使用するため、適切な using を追加または、フォームの上部にあるステートメントをインポートします。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. フォームのコンス トラクターの前の手順からセットアップ メソッドを呼び出すまたは<xref:System.Windows.Forms.Form.Load>イベント処理メソッドです。 このコードをフォームのコンス トラクターに追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. 処理、<xref:System.Windows.Forms.TreeView.NodeMouseClick>イベントを`treeview1` **、**を設定するコードを実装および`listview1`ノードがクリックされたときに、ノードの内容とします。 `Form1` クラスに次のコードを追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     C# を使用している場合があることを確認、<xref:System.Windows.Forms.TreeView.NodeMouseClick>イベント処理メソッドに関連付けられているイベントです。 このコードをフォームのコンス トラクターに追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
     含む分割フォームが表示されます、<xref:System.Windows.Forms.TreeView>左側にある、プロジェクト ディレクトリを表示するコントロールと<xref:System.Windows.Forms.ListView>3 つの列の右側にあるコントロールです。 走査することができます、<xref:System.Windows.Forms.TreeView>ディレクトリ ノードを選択して、<xref:System.Windows.Forms.ListView>選択したディレクトリの内容が格納されます。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでは、使用できる方法の例<xref:System.Windows.Forms.TreeView>と<xref:System.Windows.Forms.ListView>化を制御します。 これらのコントロールの詳細については、次のトピックを参照してください。  
  
-   [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [方法: ListView コントロールに検索機能を追加する](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [方法: ショートカット メニューを TreeView ノードに追加する](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [方法: Windows フォーム TreeView コントロールでノードを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [方法: Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
