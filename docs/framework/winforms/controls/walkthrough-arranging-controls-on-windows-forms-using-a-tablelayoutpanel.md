---
title: "チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置 | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 配置 (TableLayoutPanel を使用した)"
  - "TableLayoutPanel コントロール [Windows フォーム], チュートリアル"
  - "Windows フォーム コントロール, 配置"
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置
アプリケーションによっては、フォームのサイズを変更したり、コンテンツのサイズが変化したりしたときに、それに応じて自動的にレイアウトを調整するフォームが必要です。  動的なレイアウトが必要であり、しかも <xref:System.Windows.Forms.Control.Layout> イベントをコードで明示的に処理しない場合は、レイアウト パネルの使用を検討してください。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> コントロールや <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、コントロールをフォームに直観的に配置できます。  これら 2 つのコントロールは、それぞれに含まれる子コントロールの相対位置を制御するための自動的で設定可能な機能を提供します。また、実行時に動的なレイアウト機能を提供するため、親フォームの寸法の変更に応じて子コントロールのサイズと位置を変更できます。  また、レイアウト パネルは他のレイアウト パネルの入れ子にすることもできるため、高度なユーザー インターフェイスを実現できます。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> は、その内容を特定のフロー方向 \(水平または垂直方向\) に配置します。  このコントロールの内容は、ある行から次の行、またはある列から次の列に折り返すことができます。  また、折り返さずにクリップすることもできます。  詳細については、「[チュートリアル : FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)」を参照してください。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> は、その内容をグリッドに配置し、HTML \<table\> 要素と同じような機能を提供します。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールでは、コントロールをグリッド レイアウトに配置でき、個々のコントロールの位置を正確に指定する必要がありません。  このレイアウト パネルのセルは行と列に配置され、それぞれ異なったサイズを設定できます。  セルは、行や列にまたがって結合できます。  セルには、フォームに配置できるすべての要素を格納できる他、ほとんどの点でコンテナーとして動作します。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、実行時に比例的なサイズ変更機能を提供するため、フォームのサイズ変更に合わせてレイアウトを滑らかに変更できます。  このため、<xref:System.Windows.Forms.TableLayoutPanel> コントロールは、データ入力フォームやアプリケーションのローカライズなどに適しています。  詳細については、「[Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/ja-jp/e193b4fc-912a-4917-b036-b76c7a6f58ab)」および「[Walkthrough: Creating a Localizable Windows Form](http://msdn.microsoft.com/ja-jp/c5240b6e-aaca-4286-9bae-778a416edb9c)」を参照してください。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、通常はレイアウト全体のコンテナーとして使用しないでください。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、レイアウトの各部に比例的なサイズ変更機能を提供するために使用してください。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   行と列へのコントロールの配置  
  
-   行と列のプロパティの設定  
  
-   複数行および複数列へのコントロールの拡大  
  
-   オーバーフローの自動処理  
  
-   ツールボックスでのダブルクリックによるコントロールの挿入  
  
-   アウトラインの描画によるコントロールの挿入  
  
-   別の親コントロールへの既存コントロールの再割り当て  
  
 ここでは、これらの重要なレイアウト機能が果たす役割について理解します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### プロジェクトを作成するには  
  
1.  "TableLayoutPanelExample" という名前の Windows アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **Windows** **フォーム デザイナー**でフォームを選択します。  
  
## 行と列へのコントロールの配置  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、行や列にコントロールを簡単に配置できます。  
  
#### TableLayoutPanel を使用して、コントロールを行や列に配置するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをドラッグします。  既定では、<xref:System.Windows.Forms.TableLayoutPanel> コントロールには 4 つのセルがあります。  
  
2.  **ツールボックス**から <xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールにドラッグし、セルのいずれかにドロップします。  選択したセル内に <xref:System.Windows.Forms.Button> コントロールが作成されます。  
  
3.  さらに 3 つの <xref:System.Windows.Forms.Button> コントロールを、**ツールボックス**から <xref:System.Windows.Forms.TableLayoutPanel> コントロールにドラッグし、各セルにボタンを配置します。  
  
4.  2 つの列の間にある垂直方向のサイズ変更ハンドルをドラッグして左に移動します。  1 列目の <xref:System.Windows.Forms.Button> コントロールの幅が縮小しますが、2 列目の <xref:System.Windows.Forms.Button> コントロールのサイズは変更されません。  
  
5.  2 つの列の間にある垂直方向のサイズ変更ハンドルをドラッグして右に移動します。  1 列目の <xref:System.Windows.Forms.Button> コントロールが元のサイズに戻り、2 列目の <xref:System.Windows.Forms.Button> コントロールが右側に移動します。  
  
6.  水平方向のサイズ変更ハンドルを上下に移動し、パネル内のコントロールが受ける影響を確認します。  
  
## ドッキングおよび固定を使用した、セル内のコントロールの配置  
 <xref:System.Windows.Forms.TableLayoutPanel> の子コントロールの固定動作は、他のコンテナー コントロールの場合と異なります。  子コントロールのドッキング動作は、他のコンテナー コントロールと同じです。  
  
#### セル内のコントロールの配置  
  
1.  最初の <xref:System.Windows.Forms.Button> コントロールを選択します。  <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に変更します。  <xref:System.Windows.Forms.Button> コントロールがセル全体に拡大します。  
  
2.  他の <xref:System.Windows.Forms.Button> コントロールのいずれかを選択します。  <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を <xref:System.Windows.Forms.AnchorStyles> に変更します。  コントロールが移動し、その右側の境界線がセルの右側の境界線に近づきます。  境界間の距離は、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Margin%2A> プロパティとパネルの <xref:System.Windows.Forms.Control.Padding%2A> プロパティの合計値です。  
  
3.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を <xref:System.Windows.Forms.AnchorStyles> および <xref:System.Windows.Forms.AnchorStyles> に変更します。  コントロールのサイズが、<xref:System.Windows.Forms.Control.Margin%2A> 値と <xref:System.Windows.Forms.Control.Padding%2A> 値を考慮して、セルの幅に変更されます。  
  
4.  <xref:System.Windows.Forms.AnchorStyles> スタイルと <xref:System.Windows.Forms.AnchorStyles> スタイルを使用して、手順 2. と手順 3. を繰り返します。  
  
## 行と列のプロパティの設定  
 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> コレクションと <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> コレクションを使用して、行と列のプロパティを個別に設定できます。  
  
#### 行と列のプロパティを設定するには  
  
1.  **Windows フォーム デザイナー**で <xref:System.Windows.Forms.TableLayoutPanel> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、**\[列\]** エントリの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> コレクションを開きます。  
  
3.  最初の列を選択し、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> プロパティの値を <xref:System.Windows.Forms.SizeType> に変更します。  **\[OK\]** をクリックして変更を適用します。  最初の列の幅が、<xref:System.Windows.Forms.Button> コントロールに合わせて縮小されます。  また、列の幅が変更できなくなっていることも確認してください。  
  
4.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> コレクションを開き、最初の列を選択します。  <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> プロパティの値を <xref:System.Windows.Forms.SizeType> に変更します。  **\[OK\]** をクリックして変更を適用します。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールの幅を拡大すると、最初の列の幅が拡大します。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールの幅を縮小すると、最初の列のボタンのサイズがセルに合わせて変更されます。  また、列の幅が変更できることも確認してください。  
  
5.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> コレクションを開き、表示されているすべての列を選択します。  すべての <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> プロパティの値を <xref:System.Windows.Forms.SizeType> に設定します。  **\[OK\]** をクリックして変更を適用します。  <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> コレクションでも、この手順を繰り返します。  
  
6.  隅のサイズ変更ハンドルのいずれかをドラッグして、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの幅と高さを共に変更します。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールのサイズの変化に応じて、行と列のサイズが変更されます。  また、行と列は、水平方向と垂直方向のサイズ変更ハンドルを使用してサイズを変更できることも確認してください。  
  
## 複数行および複数列へのコントロールの拡大  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、デザイン時にいくつかの新しいプロパティをコントロールに追加します。  これらのプロパティのうちの 2 つが `RowSpan` と `ColumnSpan` です。  これら 2 つのプロパティを使用すると、コントロールを複数の行または列に拡大できます。  
  
#### コントロールを複数の行と列に拡大するには  
  
1.  最初の列の最初の行にある <xref:System.Windows.Forms.Button> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、`ColumnSpan` プロパティの値を 2 に変更します。  <xref:System.Windows.Forms.Button> コントロールが最初の列と 2 番目の列を占有します。  また、この変更に対応するために新しい行が追加されていることも確認してください。  
  
3.  `RowSpan` プロパティに対して手順 2. を繰り返します。  
  
## ツールボックスでのダブルクリックによるコントロールの挿入  
 **ツールボックス**でコントロールをダブルクリックすることにより、そのコントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールに挿入できます。  
  
#### ツールボックスでダブルクリックしてコントロールを挿入するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをドラッグします。  
  
2.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロール アイコンをダブルクリックします。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールの最初のセルに新しいボタン コントロールが表示されます。  
  
3.  **ツールボックス**でさらにいくつかのコントロールを ダブルクリックします。  新しいコントロールが <xref:System.Windows.Forms.TableLayoutPanel> コントロールの未使用のセルに順次表示されます。  また、空のセルがない場合は、新しいコントロールを格納するために <xref:System.Windows.Forms.TableLayoutPanel> コントロールが拡大します。  
  
## オーバーフローの自動処理  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールにコントロールを挿入していくと、新しいコントロールを挿入する空のセルがなくなることがあります。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、セルの数を増やすことによってこのような状況に自動的に対処します。  
  
#### オーバーフローの自動処理を観察するには  
  
1.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールに空のセルがある場合は、<xref:System.Windows.Forms.TableLayoutPanel> コントロールがいっぱいになるまで、新しい <xref:System.Windows.Forms.Button> コントロールを挿入していきます。  
  
2.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールがいっぱいになったら、**ツールボックス**の <xref:System.Windows.Forms.Button> アイコンをダブルクリックして、新しい <xref:System.Windows.Forms.Button> コントロールを挿入します。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールでは、新しいコントロールを格納する新しいセルが作成されます。  コントロールをさらにいくつか挿入し、サイズ変更動作を確認します。  
  
3.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールの <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> プロパティの値を <xref:System.Windows.Forms.TableLayoutPanelGrowStyle> に変更します。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールがいっぱいになるまで、**ツールボックス**の <xref:System.Windows.Forms.Button> アイコンをダブルクリックして、<xref:System.Windows.Forms.Button> コントロールを挿入します。  **ツールボックス**の <xref:System.Windows.Forms.Button> アイコンを再度ダブルクリックします。  追加の行と列を作成できないというエラー メッセージが **Windows フォーム デザイナー**によって表示されます。  
  
## アウトラインの描画によるコントロールの挿入  
 セルにコントロールのアウトラインを描画することによって、コントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールに挿入し、サイズを指定できます。  
  
#### アウトラインを描画してコントロールを挿入するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをドラッグします。  
  
2.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロール アイコンをクリックします。  フォームにドラッグしないでください。  
  
3.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールにマウス ポインターを置きます。  ポインターが <xref:System.Windows.Forms.Button> コントロール アイコンが付いた十字カーソルに変わります。  
  
4.  マウス ボタンを押したままにします。  
  
5.  マウス ポインターをドラッグして、<xref:System.Windows.Forms.Button> コントロールのアウトラインを描画します。  適切なサイズのアウトラインを描画したら、マウス ボタンを離します。  コントロールのアウトラインを描画したセルに <xref:System.Windows.Forms.Button> コントロールが作成されます。  
  
## 1 つのセルに配置できるコントロールの数  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールでは、セルごとに 1 つの子コントロールしか配置できません。  
  
#### セルに複数のコントロールを配置できないことを確認するには  
  
-   **ツールボックス**から <xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールにドラッグし、割り当て済みのセルのいずれかにドロップします。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールでは、割り当て済みのセルに <xref:System.Windows.Forms.Button> コントロールをドロップできないことを確認してください。  
  
## コントロールの交換  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールでは、2 つの別個のセルに割り当てられているコントロールを交換できます。  
  
#### コントロールを交換するには  
  
-   割り当て済みのセルからいずれかの <xref:System.Windows.Forms.Button> コントロールをドラッグし、別の割り当て済みセルにドロップします。  2 つのコントロールがそれぞれ他方のセルに移動します。  
  
## 次の手順  
 レイアウト パネルとコントロールを組み合わせて使用すると、複雑なレイアウトを作成できます。  次に行う作業の例を示します。  
  
-   いずれかの <xref:System.Windows.Forms.Button> コントロールのサイズを変更して、レイアウトの変化を確認します。  
  
-   選択した複数のコントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールに貼り付け、それらがどのように挿入されるかを確認します。  
  
-   レイアウト パネルには、別のレイアウト パネルを含めることができます。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールを既存のコントロールにドロップしてみます。  
  
-   <xref:System.Windows.Forms.TableLayoutPanel> コントロールを親フォームにドッキングします。  フォームのサイズを変更し、レイアウトの変化を確認します。  
  
## 参照  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [チュートリアル : FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers Redmond, WA: Microsoft Press, 1999. \(USBN: 0\-7356\-0566\-1\)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)   
 [Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/ja-jp/e193b4fc-912a-4917-b036-b76c7a6f58ab)   
 [Walkthrough: Creating a Localizable Windows Form](http://msdn.microsoft.com/ja-jp/c5240b6e-aaca-4286-9bae-778a416edb9c)   
 [TableLayoutPanel コントロールの推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)   
 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [方法 : Windows フォーム上のコントロールをドッキングする](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [方法 : Windows フォームにコントロールを固定する](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)   
 [チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)