---
title: "チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドラッグ アンド ドロップ [WPF], チュートリアル"
  - "チュートリアル [WPF], ドラッグ アンド ドロップ"
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化
このチュートリアルでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でドラッグ アンド ドロップによるデータ転送に参加できるカスタム ユーザー コントロールを作成する方法を説明します。  
  
 このチュートリアルでは、円を表すカスタム WPF <xref:System.Windows.Controls.UserControl> を作成します。  コントロールに機能を実装して、ドラッグ アンド ドロップ操作でデータを転送できるようにします。  たとえば、ある Circle コントロールから別のコントロールにドラッグすると、塗りつぶしの色のデータがソースの Circle からターゲットにコピーされます。  Circle コントロールから <xref:System.Windows.Controls.TextBox> にドラッグすると、塗りつぶしの色の文字列形式が <xref:System.Windows.Controls.TextBox> にコピーされます。  2 つのパネル コントロールを含む小さなアプリケーションおよび <xref:System.Windows.Controls.TextBox> も作成して、ドラッグ アンド ドロップ機能をテストします。  また、ドロップした Circle データをパネルで処理できるようにするコードを記述します。これにより、あるパネルの子コレクションから別の場所に Circle を移動またはコピーできるようになります。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   カスタム ユーザー コントロールを作成する。  
  
-   ユーザー コントロールがドラッグ ソースになるようにする。  
  
-   ユーザー コントロールがドロップ ターゲットになるようにする。  
  
-   ユーザー コントロールからドロップされたデータをパネルで受け取ることができるようにする。  
  
## 必要条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   Visual Studio 2010  
  
## アプリケーション プロジェクトの作成  
 このセクションでは、2 つのパネルを備えたメイン ページおよび <xref:System.Windows.Controls.TextBox> が含まれるアプリケーション インフラストラクチャを作成します。  
  
### プロジェクトを作成するには  
  
1.  Visual Basic または Visual C\# で `DragDropExample` という名前の新しい WPF アプリケーション プロジェクトを作成します。  詳細については、「[方法 : 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/ja-jp/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)」を参照してください。  
  
2.  MainWindow.xaml を開きます。  
  
3.  <xref:System.Windows.Controls.Grid> の開始タグと終了タグの間に、次のマークアップを追加します。  
  
     このマークアップは、テスト アプリケーションのユーザー インターフェイスを作成します。  
  
     [!code-xml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## プロジェクトへの新しいユーザー コントロールの追加  
 ここでは、プロジェクトに新しいユーザー コントロールを追加します。  
  
### 新しいユーザー コントロールを追加するには  
  
1.  \[プロジェクト\] メニューの **\[ユーザー コントロールの追加\]** をクリックします。  
  
2.  \[新しい項目の追加\] ダイアログ ボックスで、名前を `Circle.xaml` に変更し、**\[追加\]** をクリックします。  
  
     Circle.xaml とその分離コードがプロジェクトに追加されます。  
  
3.  Circle.xaml を開きます。  
  
     このファイルには、ユーザー コントロールのユーザー インターフェイス要素が含まれます。  
  
4.  次のマークアップをルート <xref:System.Windows.Controls.Grid> に追加し、青い円を UI とした単純なユーザー コントロールを作成します。  
  
     [!code-xml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
6.  C\# で、既定のコンストラクターの後に次のコードを追加して、コピー コンストラクターを作成します。  Visual Basic で、次のコードを追加して、既定のコンストラクターとコピー コンストラクターの両方を作成します。  
  
     ユーザー コントロールをコピーできるようにするために、分離コード ファイルで、コピー コンストラクター メソッドを追加します。  簡素化された Circle ユーザー コントロールでは、塗りつぶしとユーザー コントロールのサイズのみをコピーします。  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### メイン ウィンドウにユーザー コントロールを追加するには  
  
1.  MainWindow.xaml を開きます。  
  
2.  次の XAML を <xref:System.Windows.Window> の開始タグに追加して、現在のアプリケーションへの XML 名前空間参照を作成します。  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  最初の <xref:System.Windows.Controls.StackPanel> で、次の XAML を追加して、最初のパネルに Circle ユーザー コントロールの 2 つのインスタンスを作成します。  
  
     [!code-xml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     パネルの完全な XAML は次のようになります。  
  
     [!code-xml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## ユーザー コントロールでのドラッグ ソース イベントの実装  
 ここでは、ドラッグ ソースのイベント ハンドラーで、<xref:System.Windows.UIElement.OnMouseMove%2A> メソッドをオーバーライドして、ドラッグ アンド ドロップ操作を開始します。  
  
 ドラッグを開始すると \(マウス ボタンを押しながらマウスを動かすと\)、転送するデータを <xref:System.Windows.DataObject> にパッケージ化することになります。  ここでは、塗りつぶしの色の文字列形式、高さの double 型形式、およびコピーという 3 つのデータ項目を、Circle コントロールがパッケージ化します。  
  
### ドラッグ アンド ドロップ操作を開始するには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  次の <xref:System.Windows.UIElement.OnMouseMove%2A> オーバーライドを追加して、<xref:System.Windows.UIElement.MouseMove> イベントにクラス処理を提供します。  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     この <xref:System.Windows.UIElement.OnMouseMove%2A> オーバーライドは、次のタスクを実行します。  
  
    -   マウスを動かしながらマウスの左ボタンを押しているかどうかをチェックします。  
  
    -   Circle データを <xref:System.Windows.DataObject> にパッケージ化します。  ここでは、塗りつぶしの色、高さの double 型形式、およびコピーという 3 つのデータ項目を、Circle コントロールがパッケージ化します。  
  
    -   ドラッグ アンド ドロップ操作を開始するための静的な <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=fullName> メソッドを呼び出します。  次の 3 つのパラメーターを <xref:System.Windows.DragDrop.DoDragDrop%2A> メソッドに渡します。  
  
        -   `dragSource` – このコントロールへの参照。  
  
        -   `data` – 前のコードで作成された <xref:System.Windows.DataObject>。  
  
        -   `allowedEffects` – 有効なドラッグ アンド ドロップ操作 \(<xref:System.Windows.DragDropEffects> または <xref:System.Windows.DragDropEffects>\)。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  Circle コントロールを 1 つクリックして、パネル、他の Circle、および <xref:System.Windows.Controls.TextBox> の上にドラッグします。  <xref:System.Windows.Controls.TextBox> の上にドラッグすると、カーソルが変化して移動を示します。  
  
5.  Circle を <xref:System.Windows.Controls.TextBox> の上にドラッグしながら、Ctrl キーを押します。  カーソルが変化してコピーを示すようになります。  
  
6.  Circle を <xref:System.Windows.Controls.TextBox> にドラッグ アンド ドロップします。  Circle の塗りつぶしの色の文字列形式が <xref:System.Windows.Controls.TextBox> に追加されます。  
  
     ![Circle の塗りつぶしの色の文字列形式](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop\_ColorString")  
  
 既定では、ドラッグ アンド ドロップ操作中にカーソルが変化して、データのドロップによって適用される効果を示します。  ユーザーに示されるフィードバックは、<xref:System.Windows.UIElement.GiveFeedback> イベントを処理して別のカーソルを設定することによってカスタマイズできます。  
  
### ユーザーにフィードバックを示すには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  次の <xref:System.Windows.UIElement.OnGiveFeedback%2A> オーバーライドを追加して、<xref:System.Windows.UIElement.GiveFeedback> イベントにクラス処理を提供します。  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     この <xref:System.Windows.UIElement.OnGiveFeedback%2A> オーバーライドは、次のタスクを実行します。  
  
    -   ドロップ ターゲットの <xref:System.Windows.UIElement.DragOver> イベント ハンドラーに設定された <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> の値をチェックします。  
  
    -   <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> の値に基づいて、カスタム カーソルを設定します。  このカーソルは、データのドロップによって適用される効果についての視覚的フィードバックをユーザーに示すためのものです。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  パネル、他の Circle、および <xref:System.Windows.Controls.TextBox> の上に、Circle コントロールを 1 つドラッグします。  カーソルは、<xref:System.Windows.UIElement.OnGiveFeedback%2A> オーバーライドで指定したカスタム カーソルになっています。  
  
     ![カスタム カーソルによるドラッグ アンド ドロップ](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop\_CustomCursor")  
  
5.  <xref:System.Windows.Controls.TextBox> で `green` というテキストを選択します。  
  
6.  `green` というテキストを Circle コントロールにドラッグします。  既定のカーソルが表示されて、ドラッグ アンド ドロップ操作の効果を示します。  フィードバックのカーソルは、常にドラッグ ソースによって設定されます。  
  
## ユーザー コントロールでのドロップ ターゲット イベントの実装  
 ここでは、ユーザー コントロールがドロップ ターゲットであることを指定し、ユーザー コントロールがドロップ ターゲットになるようにするメソッドをオーバーライドして、ドロップするデータを処理します。  
  
### ユーザー コントロールがドロップ ターゲットになるようにするには  
  
1.  Circle.xaml を開きます。  
  
2.  <xref:System.Windows.Controls.UserControl> の開始タグで、<xref:System.Windows.UIElement.AllowDrop%2A> プロパティを追加して `true` に設定します。  
  
     [!code-xml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <xref:System.Windows.UIElement.AllowDrop%2A> プロパティが `true` に設定され、ドラッグ ソースのデータが Circle ユーザー コントロール上にドロップされると、<xref:System.Windows.UIElement.OnDrop%2A> メソッドが呼び出されます。  この方法では、ドロップされたデータを処理して、そのデータを Circle に適用します。  
  
### ドロップされたデータを処理するには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  次の <xref:System.Windows.UIElement.OnDrop%2A> オーバーライドを追加して、<xref:System.Windows.UIElement.Drop> イベントにクラス処理を提供します。  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     この <xref:System.Windows.UIElement.OnDrop%2A> オーバーライドは、次のタスクを実行します。  
  
    -   <xref:System.Windows.DataObject.GetDataPresent%2A> メソッドを使用して、ドラッグされたデータに文字列オブジェクトが含まれているかどうかをチェックします。  
  
    -   <xref:System.Windows.DataObject.GetData%2A> メソッドを使用して、文字列データが存在する場合はその文字列データを抽出します。  
  
    -   <xref:System.Windows.Media.BrushConverter> を使用して、文字列から <xref:System.Windows.Media.Brush> への変換を試みます。  
  
    -   変換が成功した場合は、Circle コントロールの UI を提供する <xref:System.Windows.Shapes.Ellipse> の <xref:System.Windows.Shapes.Shape.Fill%2A> にそのブラシを適用します。  
  
    -   <xref:System.Windows.UIElement.Drop> イベントを処理済みとしてマークします。  ドロップ イベントが Circle ユーザー コントロールによって処理済みであることをこのドロップ イベントを受け取る他の要素で認識できるようにするために、ドロップ イベントを処理済みとしてマークする必要があります。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  <xref:System.Windows.Controls.TextBox> で `green` というテキストを選択します。  
  
5.  このテキストを Circle コントロールにドラッグしてドロップします。  Circle が青から緑に変わります。  
  
     ![ブラシへの文字列の変換](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop\_DropGreenText")  
  
6.  `green` というテキストを <xref:System.Windows.Controls.TextBox> に入力します。  
  
7.  <xref:System.Windows.Controls.TextBox> で `gre` というテキストを選択します。  
  
8.  このテキストを Circle コントロールにドラッグしてドロップします。  カーソルが変化し、ドロップが有効であることが示されますが、`gre` は有効な色ではないので Circle の色は変わりません。  
  
9. 緑の Circle コントロールからドラッグして、青の Circle コントロールにドロップします。  Circle が青から緑に変わります。  表示されるカーソルは、<xref:System.Windows.Controls.TextBox> または Circle のどちらがドラッグ ソースであるかによって異なります。  
  
 ある要素をドロップ ターゲットにするために必要なことは、<xref:System.Windows.UIElement.AllowDrop%2A> プロパティを `true` に設定し、ドロップされたデータを処理することです。  ただし、ユーザー エクスペリエンスを向上させるためには、<xref:System.Windows.UIElement.DragEnter>、<xref:System.Windows.UIElement.DragLeave>、および <xref:System.Windows.UIElement.DragOver> の各イベントも処理する必要があります。  これらのイベントでは、データのドロップ前に、チェックを実行して追加のフィードバックをユーザーに提供することができます。  
  
 データが Circle ユーザー コントロール上にドラッグされると、このコントロールは、ドラッグされたデータが処理可能であるかどうかをドラッグ ソースに通知します。  このコントロールは、データの処理方法が不明な場合、ドロップを拒否します。  これを行うには、<xref:System.Windows.UIElement.DragOver> イベントを処理して、<xref:System.Windows.DragEventArgs.Effects%2A> プロパティを設定します。  
  
### データ ドロップが有効であることを確認するには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  次の <xref:System.Windows.UIElement.OnDragOver%2A> オーバーライドを追加して、<xref:System.Windows.UIElement.DragOver> イベントにクラス処理を提供します。  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     この <xref:System.Windows.UIElement.OnDragOver%2A> オーバーライドは、次のタスクを実行します。  
  
    -   <xref:System.Windows.DragEventArgs.Effects%2A> プロパティを <xref:System.Windows.DragDropEffects> に設定します。  
  
    -   <xref:System.Windows.UIElement.OnDrop%2A> メソッドの場合と同じチェックを実行して、ドラッグされたデータを Circle ユーザー コントロールで処理できるかどうかを判断します。  
  
    -   ユーザー コントロールでデータを処理できる場合は、<xref:System.Windows.DragEventArgs.Effects%2A> プロパティを <xref:System.Windows.DragDropEffects> または <xref:System.Windows.DragDropEffects> に設定します。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  <xref:System.Windows.Controls.TextBox> で `gre` というテキストを選択します。  
  
5.  このテキストを Circle コントロールにドラッグします。  カーソルが変化し、ドロップが有効でないことが示されます。これは、`gre` が有効な色ではないためです。  
  
 ドロップ操作のプレビューを適用することにより、ユーザー エクスペリエンスをさらに向上させることができます。  Circle ユーザー コントロールについて、<xref:System.Windows.UIElement.OnDragEnter%2A> メソッドと <xref:System.Windows.UIElement.OnDragLeave%2A> メソッドをオーバーライドします。  データをコントロール上にドラッグしたときに、現在の背景の <xref:System.Windows.Shapes.Shape.Fill%2A> がプレースホルダーの変数に保存されます。  その文字列がブラシに変換されて、Circle の UI を提供する <xref:System.Windows.Shapes.Ellipse> に適用されます。  データがドロップされることなく Circle の外へドラッグされると、元の <xref:System.Windows.Shapes.Shape.Fill%2A> の値が Circle に再び適用されます。  
  
### ドラッグ アンド ドロップ操作の効果をプレビューするには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  Circle クラスで、`_previousFill` という名前のプライベート <xref:System.Windows.Media.Brush> 変数を宣言し、`null` に初期化します。  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  次の <xref:System.Windows.UIElement.OnDragEnter%2A> オーバーライドを追加して、<xref:System.Windows.UIElement.DragEnter> イベントにクラス処理を提供します。  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     この <xref:System.Windows.UIElement.OnDragEnter%2A> オーバーライドは、次のタスクを実行します。  
  
    -   <xref:System.Windows.Shapes.Ellipse> の <xref:System.Windows.Shapes.Shape.Fill%2A> プロパティを `_previousFill` 変数に保存します。  
  
    -   <xref:System.Windows.UIElement.OnDrop%2A> メソッドの場合と同じチェックを実行して、データを <xref:System.Windows.Media.Brush> に変換できるかどうかを判断します。  
  
    -   データが有効な <xref:System.Windows.Media.Brush> に変換される場合は、<xref:System.Windows.Shapes.Ellipse> の <xref:System.Windows.Shapes.Shape.Fill%2A> に適用します。  
  
4.  次の <xref:System.Windows.UIElement.OnDragLeave%2A> オーバーライドを追加して、<xref:System.Windows.UIElement.DragLeave> イベントにクラス処理を提供します。  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     この <xref:System.Windows.UIElement.OnDragLeave%2A> オーバーライドは、次のタスクを実行します。  
  
    -   `_previousFill` 変数に保存された <xref:System.Windows.Media.Brush> を、Circle ユーザー コントロールの UI を提供する <xref:System.Windows.Shapes.Ellipse> の <xref:System.Windows.Shapes.Shape.Fill%2A> に適用します。  
  
5.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
6.  <xref:System.Windows.Controls.TextBox> で `green` というテキストを選択します。  
  
7.  このテキストを Circle コントロール上にドラッグしますが、ドロップしません。  Circle が青から緑に変わります。  
  
     ![ドラッグ アンド ドロップ操作の効果のプレビュー](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop\_PreviewEffects")  
  
8.  このテキストを Circle コントロールから離れた位置にドラッグします。  Circle が緑から青に戻ります。  
  
## ドロップされたデータをパネルで受け取ることの有効化  
 ここでは、Circle ユーザー コントロールをホストするパネルを、ドラッグされた Circle データのドロップ ターゲットとして機能するようにします。  あるパネルから別のパネルに Circle を移動すること、または Ctrl キーを押しながら Circle をドラッグ アンド ドロップして Circle コントロールのコピーを作成することを可能にするコードを実装します。  
  
### パネルがドロップ ターゲットになるようにするには  
  
1.  MainWindow.xaml を開きます。  
  
2.  次の XAML に示すように、それぞれの <xref:System.Windows.Controls.StackPanel> コントロールで、<xref:System.Windows.UIElement.DragOver> イベントおよび <xref:System.Windows.UIElement.Drop> イベント用のハンドラーを追加します。  <xref:System.Windows.UIElement.DragOver> イベント ハンドラーに `panel_DragOver` という名前、<xref:System.Windows.UIElement.Drop> イベント ハンドラーに `panel_Drop` という名前を付けます。  
  
     [!code-xml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  MainWindows.xaml.cs または MainWindow.xaml.vb を開きます。  
  
4.  <xref:System.Windows.UIElement.DragOver> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     この <xref:System.Windows.UIElement.DragOver> イベント ハンドラーは、次のタスクを実行します。  
  
    -   Circle ユーザー コントロールによって <xref:system.Windows.DataObject> にパッケージ化され、<xref:System.Windows.DragDrop.DoDragDrop%2A> の呼び出しに渡される "オブジェクト" データが、ドラッグされたデータに含まれていることをチェックします。  
  
    -   "オブジェクト" データがある場合は、Ctrl キーが押されているかどうかをチェックします。  
  
    -   Ctrl キーが押されている場合は、<xref:System.Windows.DragEventArgs.Effects%2A> プロパティを <xref:System.Windows.DragDropEffects> に設定します。  それ以外の場合は、<xref:System.Windows.DragEventArgs.Effects%2A> プロパティを <xref:System.Windows.DragDropEffects> に設定します。  
  
5.  <xref:System.Windows.UIElement.Drop> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     この <xref:System.Windows.UIElement.Drop> イベント ハンドラーは、次のタスクを実行します。  
  
    -   <xref:System.Windows.UIElement.Drop> イベントが処理されたかどうかをチェックします。  たとえば、ある Circle が <xref:System.Windows.UIElement.Drop> イベントを処理する別の Circle 上にドロップされた場合、その Circle を含むパネルではイベントを処理しないようにしたいと考えるものです。  
  
    -   <xref:System.Windows.UIElement.Drop> イベントが処理されない場合は、Ctrl キーが押されているかどうかをチェックします。  
  
    -   <xref:System.Windows.UIElement.Drop> イベントの発生時に Ctrl キーが押されている場合は、Circle コントロールのコピーを作成して、<xref:System.Windows.Controls.StackPanel> の <xref:System.Windows.Controls.Panel.Children%2A> コレクションに追加します。  
  
    -   Ctrl キーが押されていない場合は、Circle を親パネルの <xref:System.Windows.Controls.Panel.Children%2A> コレクションから、ドロップ先のパネルの <xref:System.Windows.Controls.Panel.Children%2A> コレクションに移動します。  
  
    -   <xref:System.Windows.DragEventArgs.Effects%2A> プロパティを設定して、移動操作またはコピー操作が実行されたことを <xref:System.Windows.DragDrop.DoDragDrop%2A> メソッドに通知します。  
  
6.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
7.  <xref:System.Windows.Controls.TextBox> で `green` というテキストを選択します。  
  
8.  このテキストを Circle コントロール上にドラッグしてドロップします。  
  
9. Circle コントロールを左側のパネルから右側のパネルにドラッグしてドロップします。  Circle が、左側のパネルの <xref:System.Windows.Controls.Panel.Children%2A> コレクションから削除され、右側のパネルの子コレクションに追加されます。  
  
10. Ctrl キーを押しながら、Circle コントロールがあるパネルから別のパネルに Circle コントロールをドラッグしてドロップします。  Circle がコピーされ、そのコピーが、受け取る側のパネルの <xref:System.Windows.Controls.Panel.Children%2A> コレクションに追加されます。  
  
     ![Ctrl キーを押しながら Circle をドラッグ](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop\_PanelDrop")  
  
## 参照  
 [ドラッグ アンド ドロップの概要](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)