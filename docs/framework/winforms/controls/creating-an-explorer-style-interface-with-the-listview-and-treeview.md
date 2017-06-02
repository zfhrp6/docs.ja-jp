---
title: "チュートリアル : デザイナーを使用した、ListView コントロールと TreeView コントロールを含むエクスプローラー スタイルのインターフェイスの作成 | Microsoft Docs"
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
  - "エクスプローラー スタイル アプリケーション"
  - "エクスプローラー スタイル アプリケーション, チュートリアル"
  - "ListView コントロール [Windows フォーム], エクスプローラー スタイルのインターフェイス"
  - "ListView コントロール [Windows フォーム], エクスプローラー スタイル インターフェイス"
  - "ListView コントロール [Windows フォーム], TreeView コントロールで使用する"
  - "TreeView コントロール [Windows フォーム], ListView コントロールで使用する"
  - "TreeView コントロール [Windows フォーム], 使用 (エクスプローラー スタイルのインターフェイスで)"
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# チュートリアル : デザイナーを使用した、ListView コントロールと TreeView コントロールを含むエクスプローラー スタイルのインターフェイスの作成
Visual Studio の利点の 1 つは、プロフェッショナルなデザインの Windows フォーム アプリケーションを短時間で作成できることです。  一般的なシナリオは、Windows オペレーティング システムの Windows エクスプローラーによく似た、<xref:System.Windows.Forms.ListView> コントロールと <xref:System.Windows.Forms.TreeView> コントロールを持つユーザー インターフェイス \(UI\) を作成することです。  Windows エクスプローラーは、ユーザーのコンピューターに格納されているファイルとフォルダーを階層構造で表示します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### ListView コントロールと TreeView コントロールを含むフォームを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで以下の作業を行います。  
  
    1.  カテゴリで **\[Visual Basic\]** または **\[Visual C\#\]** を選択します。  
  
    2.  テンプレートの一覧で、**\[Windows フォーム アプリケーション\]** を選択します。  
  
3.  **\[OK\]** をクリックします。  新しい Windows フォーム プロジェクトが作成されます。  
  
4.  フォームに <xref:System.Windows.Forms.SplitContainer> コントロールを追加し、<xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
5.  `imageList1` という名前の <xref:System.Windows.Forms.ImageList> をフォームに追加し、プロパティ ウィンドウを使用して、フォルダー イメージとドキュメント イメージの 2 つのイメージをこの順に追加します。  
  
6.  `treeview1` という名前の <xref:System.Windows.Forms.TreeView> をフォームに追加し、<xref:System.Windows.Forms.SplitContainer> コントロールの左側に配置します。  `treeView1` のプロパティ ウィンドウで、次の手順を実行します。  
  
    1.  <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
    2.  <xref:System.Windows.Forms.TreeView.ImageList%2A> プロパティを `imagelist1` に設定します。  
  
7.  `listView1` という名前の <xref:System.Windows.Forms.ListView> をフォームに追加し、<xref:System.Windows.Forms.SplitContainer> コントロールの右側に配置します。  `listview1` のプロパティ ウィンドウで、次の手順を実行します。  
  
    1.  <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
    2.  <xref:System.Windows.Forms.ListView.View%2A> プロパティを <xref:System.Windows.Forms.View> に設定します。  
  
    3.  <xref:System.Windows.Forms.ListView.Columns%2A> プロパティの省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして、ColumnHeader コレクション エディターを開きます。3 つの列を追加し、<xref:System.Windows.Forms.ColumnHeader.Text%2A> プロパティをそれぞれ `Name`、`Type`、`Last Modified` に設定します。  **\[OK\]** をクリックし、ダイアログ ボックスを閉じます。  
  
    4.  <xref:System.Windows.Forms.ListView.SmallImageList%2A> プロパティを `imageList1.` に設定します。  
  
8.  <xref:System.Windows.Forms.TreeView> にノードとサブノードを設定するコードを実装します。  `Form1` クラスに次のコードを追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. このコードでは System.IO 名前空間を使用しているため、フォームの先頭に適切な using ステートメントまたはインポート ステートメントを追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. フォームのコンストラクターまたは <xref:System.Windows.Forms.Form.Load> イベント処理メソッドから、前の手順で作成したセットアップ メソッドを呼び出します。  次のコードをフォーム コンストラクターに追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. `treeview1` の <xref:System.Windows.Forms.TreeView.NodeMouseClick> イベントを処理し、ノードがクリックされたときにノードの内容を `listview1` に設定するコードを実装します。  `Form1` クラスに次のコードを追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     C\# を使用している場合は、<xref:System.Windows.Forms.TreeView.NodeMouseClick> イベントをそのイベント処理メソッドに関連付けてください。  次のコードをフォーム コンストラクターに追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### フォームをテストするには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
     プロジェクト ディレクトリを表示する <xref:System.Windows.Forms.TreeView> コントロールが左側にあり、3 つの列が含まれた <xref:System.Windows.Forms.ListView> コントロールが右側にある分割フォームが表示されます。  ディレクトリ ノードを選択して <xref:System.Windows.Forms.TreeView> を走査すると、選択したディレクトリの内容が <xref:System.Windows.Forms.ListView> に表示されます。  
  
## 次の手順  
 このアプリケーションは、<xref:System.Windows.Forms.TreeView> コントロールと <xref:System.Windows.Forms.ListView> コントロールを一緒に使用する方法の一例です。  これらのコントロールの詳細については、次のトピックを参照してください。  
  
-   [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [方法 : ListView コントロールに検索機能を追加する](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [方法 : ショートカット メニューを TreeView ノードに追加する](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## 参照  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.TreeView>   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [方法 : Windows フォーム TreeView コントロールでノードを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)   
 [方法 : Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)