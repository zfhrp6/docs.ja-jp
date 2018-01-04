---
title: "チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e413a7ddf7e256538e56876712a54f875392b59a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化
このチュートリアルでのドラッグ アンド ドロップのデータ転送に含めることができるカスタム ユーザー コントロールを作成する方法を示します[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。  
  
 このチュートリアルでは、カスタムの WPF を作成します<xref:System.Windows.Controls.UserControl>を表す円を選択します。 ドラッグ アンド ドロップ経由のデータ転送を有効にするコントロールの機能を実装します。 たとえば、別に 1 つの円コントロールからドラッグした場合の塗りつぶしの色データがソースからコピー、円ターゲットにします。 円コントロールからドラッグした場合、 <xref:System.Windows.Controls.TextBox>、塗りつぶしの色の文字列形式にコピー、<xref:System.Windows.Controls.TextBox>です。 2 つのパネル コントロールが含まれた小さなアプリケーションを作成することも、および<xref:System.Windows.Controls.TextBox>ドラッグ アンド ドロップ機能をテストします。 移動または 1 つのパネルの子のコレクションから、他の円をコピーすることができますが、削除された円のデータを処理するパネルをできるようにするコードを記述します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   カスタム ユーザー コントロールを作成します。  
  
-   ドラッグ元であるユーザー コントロールを有効にします。  
  
-   ドロップ ターゲットにするユーザー コントロールを有効にします。  
  
-   ユーザー コントロールから削除されるデータを受信するパネルを有効にします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   Visual Studio 2010  
  
## <a name="creating-the-application-project"></a>アプリケーション プロジェクトの作成  
 このセクションでは、2 つのパネルでのメイン ページが含まれるアプリケーション インフラストラクチャを作成します、<xref:System.Windows.Controls.TextBox>です。  
  
### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  Visual Basic または Visual c# のという名前の新しい WPF アプリケーション プロジェクトを作成する`DragDropExample`です。 詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。  
  
2.  MainWindow.xaml を開きます。  
  
3.  開始タグと終了の間で、次のマークアップを追加<xref:System.Windows.Controls.Grid>タグ。  
  
     このマークアップでは、テスト アプリケーションのユーザー インターフェイスを作成します。  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a>プロジェクトに新しいユーザー コントロールの追加  
 このセクションでは、プロジェクトに新しいユーザー コントロールを追加します。  
  
### <a name="to-add-a-new-user-control"></a>新しいユーザー コントロールを追加するには  
  
1.  [プロジェクト] メニューで、次のように選択します。**ユーザー コントロールの追加**です。  
  
2.  新しい項目の追加 ダイアログ ボックスに名前を変更`Circle.xaml`、 をクリック**追加**です。  
  
     Circle.xaml とその分離コードは、プロジェクトに追加されます。  
  
3.  Circle.xaml を開きます。  
  
     このファイルは、ユーザー コントロールのユーザー インターフェイス要素が格納されます。  
  
4.  ルートに、次のマークアップを追加<xref:System.Windows.Controls.Grid>UI として青い円形のある単純なユーザー コントロールを作成します。  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
6.  C# の場合は、既定のコンス トラクターとコピー コンス トラクターを作成した後、次のコードを追加します。 Visual basic では、既定のコンス トラクターとコピー コンス トラクターの両方を作成するには、次のコードを追加します。  
  
     コピーするユーザー コントロールをできるようにするのには、分離コード ファイルにコピー コンス トラクター メソッドを追加します。 簡略化された円のユーザー コントロールではのみ塗りつぶしおよびコピーのサイズ、ユーザー コントロールのです。  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a>メイン ウィンドウにユーザー コントロールを追加するには  
  
1.  MainWindow.xaml を開きます。  
  
2.  次の XAML を開くときに追加<xref:System.Windows.Window>タグを現在のアプリケーションへの XML 名前空間参照を作成します。  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  最初の<xref:System.Windows.Controls.StackPanel>、最初のパネルで、円のユーザー コントロールの 2 つのインスタンスを作成する次の XAML を追加します。  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     パネルのすべての XAML は、次のようになります。  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a>ユーザー コントロールでドラッグ ソース イベントを実装します。  
 上書きは、このセクションで、<xref:System.Windows.UIElement.OnMouseMove%2A>メソッドと、ドラッグ アンド ドロップ操作を開始します。  
  
 場合は、ドラッグを開始 (マウス ボタンが押され、マウスを移動) に転送されるデータをパッケージ化は、<xref:System.Windows.DataObject>です。 ここでは、円コントロールはパッケージの 3 つのデータ項目塗りつぶしの色の高さの double 型の表現とそれ自体のコピーの文字列形式。  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a>ドラッグ アンド ドロップ操作を開始するには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  次の追加<xref:System.Windows.UIElement.OnMouseMove%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.MouseMove>イベント。  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     これは、<xref:System.Windows.UIElement.OnMouseMove%2A>オーバーライドは、次のタスクを実行します。  
  
    -   マウスの移動中に、マウスの左ボタンが押されたかどうかを確認します。  
  
    -   パッケージの円にデータを<xref:System.Windows.DataObject>です。 ここでは、次の 3 つのデータ項目のパッケージ円コントロール塗りつぶしの色の高さの double 型の表現とそれ自体のコピーの文字列形式。  
  
    -   静的なを呼び出して<xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>をドラッグ アンド ドロップ操作を開始するメソッド。 次の 3 つのパラメーターを渡す、<xref:System.Windows.DragDrop.DoDragDrop%2A>メソッド。  
  
        -   `dragSource`– このコントロールへの参照。  
  
        -   `data`–<xref:System.Windows.DataObject>前のコードで作成します。  
  
        -   `allowedEffects`– の許可されているドラッグ アンド ドロップ操作<xref:System.Windows.DragDropEffects.Copy>または<xref:System.Windows.DragDropEffects.Move>です。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  円コントロールのいずれかをクリックし、その他の円、パネル上にドラッグし、<xref:System.Windows.Controls.TextBox>です。 ドラッグしたとき、<xref:System.Windows.Controls.TextBox>カーソルが移動を示すために変わります。  
  
5.  経由で Circle をドラッグするときに、 <xref:System.Windows.Controls.TextBox>、CTRL キーを押します。 コピーを示すために、カーソルがどのように変化するかに注意してください。  
  
6.  ドラッグ アンド ドロップ上の円、<xref:System.Windows.Controls.TextBox>です。 円の塗りつぶしの色の文字列形式を追加、<xref:System.Windows.Controls.TextBox>です。  
  
     ![Circle の塗りつぶしの色の文字列表現](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")  
  
 既定では、カーソルは、データのドロップ効果が起こるかになりますを示すためにドラッグ アンド ドロップ操作中に変更されます。 処理することにより、ユーザーに指定されたフィードバックをカスタマイズすることができます、<xref:System.Windows.UIElement.GiveFeedback>イベントと異なるカーソルを設定します。  
  
### <a name="to-give-feedback-to-the-user"></a>ユーザーにフィードバックできる  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  次の追加<xref:System.Windows.UIElement.OnGiveFeedback%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.GiveFeedback>イベント。  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     これは、<xref:System.Windows.UIElement.OnGiveFeedback%2A>オーバーライドは、次のタスクを実行します。  
  
    -   チェック、<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>ドロップ ターゲットに設定されている値<xref:System.Windows.UIElement.DragOver>イベント ハンドラー。  
  
    -   基づくカスタム カーソル設定、<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>値。 カーソルはについてどのような影響がデータを削除するには、ユーザーに視覚的なフィードバックを提供するためのものです。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  パネル、他の円を統制、円の 1 つをドラッグし、<xref:System.Windows.Controls.TextBox>です。 カーソルがで指定したカスタムのカーソルでになっていることを確認、<xref:System.Windows.UIElement.OnGiveFeedback%2A>をオーバーライドします。  
  
     ![カスタム カーソルによるドラッグ アンド ドロップ](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")  
  
5.  テキスト選択`green`から、<xref:System.Windows.Controls.TextBox>です。  
  
6.  ドラッグ、`green`円コントロールにテキストです。 既定のカーソルをドラッグ アンド ドロップ操作の効果を示すために表示されていることを確認します。 フィードバックのカーソルは、ドラッグ ソースが常に設定されます。  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a>ユーザー コントロールにドロップ対象のイベントを実装します。  
 このセクションでは、ユーザー コントロールがドロップ ターゲット、オーバーライドにより、ユーザーは、メソッドがドロップ ターゲットにするのに制御し、データの削除を処理を指定します。  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>ドロップ ターゲットにするユーザー コントロールを有効にするには  
  
1.  Circle.xaml を開きます。  
  
2.  開く際に<xref:System.Windows.Controls.UserControl>タグ、追加、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティに設定し、`true`です。  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <xref:System.Windows.UIElement.OnDrop%2A>メソッドが呼び出されます、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティに設定されている`true`円ユーザー コントロール、ドラッグ ソースからのデータが削除されるとします。 このメソッドでは、削除されたデータを処理し、データを円に適用します。  
  
### <a name="to-process-the-dropped-data"></a>削除されたデータを処理するには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  次の追加<xref:System.Windows.UIElement.OnDrop%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.Drop>イベント。  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     これは、<xref:System.Windows.UIElement.OnDrop%2A>オーバーライドは、次のタスクを実行します。  
  
    -   使用して、<xref:System.Windows.DataObject.GetDataPresent%2A>メソッドをドラッグしたデータに、文字列オブジェクトが含まれているかどうかは確認します。  
  
    -   使用して、<xref:System.Windows.DataObject.GetData%2A>メソッドが存在する場合は、文字列データを抽出します。  
  
    -   使用して、<xref:System.Windows.Media.BrushConverter>を文字列に変換しようとする、<xref:System.Windows.Media.Brush>です。  
  
    -   変換が成功した場合は、適用するブラシ、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>円コントロールの UI を提供します。  
  
    -   マーク、<xref:System.Windows.UIElement.Drop>イベントを処理します。 このイベントを受け取るその他の要素は、円のユーザー コントロールにそれが処理されることが認識されるように処理済みとしては、ドロップ イベントをマークする必要があります。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  テキスト選択`green`で、<xref:System.Windows.Controls.TextBox>です。  
  
5.  円のコントロールにテキストをドラッグ アンド ドロップします。 円は、blue から緑色に変わります。  
  
     ![ブラシに文字列を変換](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")  
  
6.  テキスト入力`green`で、<xref:System.Windows.Controls.TextBox>です。  
  
7.  テキスト選択`gre`で、<xref:System.Windows.Controls.TextBox>です。  
  
8.  円コントロールにドラッグし、それをドロップします。 通知を削除可能ですが、円の色は変更されませんを示すために、カーソルが変化する`gre`は有効な色ではありません。  
  
9. 緑色の円コントロールからドラッグし、青の円コントロール上にドロップします。 円は、blue から緑色に変わります。 カーソルが表示されるかどうかに依存する通知、<xref:System.Windows.Controls.TextBox>円は、ドラッグ ソースまたはします。  
  
 設定、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティを`true`要素をドロップ ターゲットを有効にするために必要なものがドロップされたデータを処理します。 ただしより優れたユーザー エクスペリエンスを提供する必要がありますも処理する、 <xref:System.Windows.UIElement.DragEnter>、 <xref:System.Windows.UIElement.DragLeave>、および<xref:System.Windows.UIElement.DragOver>イベント。 これらのイベントでは、チェックを実行し、データが削除される前に、ユーザーにその他のフィードバックを提供できます。  
  
 円ユーザー コントロールの上のデータをドラッグすると場合、コントロールはドラッグされるデータを処理できるかどうか、ドラッグ ソースで通知する必要があります。 コントロールがデータを処理する方法を知らない場合は、ドロップを拒否する必要があります。 これを行うには処理、<xref:System.Windows.UIElement.DragOver>イベントとセット、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティです。  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a>データの削除が許可されていることを確認するには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  次の追加<xref:System.Windows.UIElement.OnDragOver%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.DragOver>イベント。  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     これは、<xref:System.Windows.UIElement.OnDragOver%2A>オーバーライドは、次のタスクを実行します。  
  
    -   <xref:System.Windows.DragEventArgs.Effects%2A> プロパティを <xref:System.Windows.DragDropEffects.None> に設定します。  
  
    -   実行される同じチェックを実行、<xref:System.Windows.UIElement.OnDrop%2A>円ユーザー コントロールがドラッグしたデータを処理できるかどうかを調べます。  
  
    -   ユーザー コントロールには、データを処理できますが、設定、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Copy>または<xref:System.Windows.DragDropEffects.Move>です。  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  テキスト選択`gre`で、<xref:System.Windows.Controls.TextBox>です。  
  
5.  円のコントロールにテキストをドラッグします。 カーソルは、ために、ボックスの一覧が使用できないことを示すために今すぐ変更通知`gre`は有効な色ではありません。  
  
 さらに、drop 操作のプレビューを適用することにより、ユーザー エクスペリエンスを強化できます。 円ユーザー コントロールが無効にする、<xref:System.Windows.UIElement.OnDragEnter%2A>と<xref:System.Windows.UIElement.OnDragLeave%2A>メソッドです。 コントロールを現在の背景の上にデータをドラッグするときに<xref:System.Windows.Shapes.Shape.Fill%2A>はプレース ホルダー変数に保存します。 文字列は、ブラシに変換しに適用される、<xref:System.Windows.Shapes.Ellipse>円を提供する UI。 場合は、データがドロップされず、元の円外にドラッグされた<xref:System.Windows.Shapes.Shape.Fill%2A>値は、円を再適用します。  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>ドラッグ アンド ドロップ操作の効果をプレビューするには  
  
1.  Circle.xaml.cs または Circle.xaml.vb を開きます。  
  
2.  円クラスで宣言プライベート<xref:System.Windows.Media.Brush>という名前の変数`_previousFill`し初期化`null`です。  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  次の追加<xref:System.Windows.UIElement.OnDragEnter%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.DragEnter>イベント。  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     これは、<xref:System.Windows.UIElement.OnDragEnter%2A>オーバーライドは、次のタスクを実行します。  
  
    -   保存、<xref:System.Windows.Shapes.Shape.Fill%2A>のプロパティ、<xref:System.Windows.Shapes.Ellipse>で、`_previousFill`変数。  
  
    -   実行される同じチェックを実行、<xref:System.Windows.UIElement.OnDrop%2A>にデータを変換できるかどうかを決定するメソッド、<xref:System.Windows.Media.Brush>です。  
  
    -   有効なデータが変換される場合<xref:System.Windows.Media.Brush>、それを適用、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>です。  
  
4.  次の追加<xref:System.Windows.UIElement.OnDragLeave%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.DragLeave>イベント。  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     これは、<xref:System.Windows.UIElement.OnDragLeave%2A>オーバーライドは、次のタスクを実行します。  
  
    -   適用される、<xref:System.Windows.Media.Brush>に保存されている、`_previousFill`変数を<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>円ユーザー コントロールの UI を提供します。  
  
5.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
6.  テキスト選択`green`で、<xref:System.Windows.Controls.TextBox>です。  
  
7.  円コントロールの上にドロップせず、テキストをドラッグします。 円は、blue から緑色に変わります。  
  
     ![ドラッグ &#45; の効果のプレビューおよび &#45; ドロップ](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")  
  
8.  円コントロールのテキストをドラッグします。 円を青に緑のバックアップから変更します。  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a>データを受信するパネルを有効にすると削除  
 このセクションでは、ドラッグしたデータのマークのドロップ ターゲットとして機能する円のユーザー コントロールをホストしているパネルを有効になります。 使用すると、円を 1 つのパネルから、別に移動するか、CTRL キーを押しながらドラッグ アンド ドロップ、円、円のコントロールのコピーを作成するコードを実装します。  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a>ドロップ ターゲットにするのには、パネルを有効にするには  
  
1.  MainWindow.xaml を開きます。  
  
2.  それぞれで、次の XAML のように、<xref:System.Windows.Controls.StackPanel>のハンドラーを追加、コントロール、<xref:System.Windows.UIElement.DragOver>と<xref:System.Windows.UIElement.Drop>イベント。 名前、<xref:System.Windows.UIElement.DragOver>イベント ハンドラー、 `panel_DragOver`、し、名前、<xref:System.Windows.UIElement.Drop>イベント ハンドラー、`panel_Drop`です。  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  MainWindows.xaml.cs または MainWindow.xaml.vb を開きます。  
  
4.  次のコードを追加、<xref:System.Windows.UIElement.DragOver>イベント ハンドラー。  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     これは、<xref:System.Windows.UIElement.DragOver>イベント ハンドラーは、次のタスクを実行します。  
  
    -   ドラッグしたデータが内にパッケージ化された"Object"データを含むことを確認、<xref:System.Windows.DataObject>円ユーザー コントロールでの呼び出しで渡されると<xref:System.Windows.DragDrop.DoDragDrop%2A>です。  
  
    -   「オブジェクト」のデータが存在する場合は、CTRL キーが押されたかどうかを確認します。  
  
    -   CTRL キーが押された場合、設定、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Copy>です。 それ以外の場合、設定、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Move>です。  
  
5.  次のコードを追加、<xref:System.Windows.UIElement.Drop>イベント ハンドラー。  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     これは、<xref:System.Windows.UIElement.Drop>イベント ハンドラーは、次のタスクを実行します。  
  
    -   チェックするかどうか、<xref:System.Windows.UIElement.Drop>イベントは既に処理されています。 たとえば、別の円が削除された場合の円をハンドル、<xref:System.Windows.UIElement.Drop>イベント、たくないもそれを処理する円を格納しているパネルです。  
  
    -   場合、<xref:System.Windows.UIElement.Drop>イベントが処理されない、チェック、CTRL キーが押されたかどうか。  
  
    -   CTRL キーが押された場合、<xref:System.Windows.UIElement.Drop>発生、円のコピーを制御およびそれを追加、<xref:System.Windows.Controls.Panel.Children%2A>のコレクション、<xref:System.Windows.Controls.StackPanel>です。  
  
    -   CTRL キーが押されていない場合から円を移動、<xref:System.Windows.Controls.Panel.Children%2A>をその親パネルのコレクション、<xref:System.Windows.Controls.Panel.Children%2A>時に削除されましたが、パネルのコレクション。  
  
    -   セット、<xref:System.Windows.DragEventArgs.Effects%2A>に通知するプロパティ、<xref:System.Windows.DragDrop.DoDragDrop%2A>メソッド移動またはコピー操作が実行されたかどうか。  
  
6.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
7.  テキスト選択`green`から、<xref:System.Windows.Controls.TextBox>です。  
  
8.  円コントロール上でテキストをドラッグ アンド ドロップします。  
  
9. 左側のパネルから、右側のパネルを円コントロールをドラッグし、ドロップします。 円はから削除、<xref:System.Windows.Controls.Panel.Children%2A>左側のパネルのコレクションと、右側のパネルの子のコレクションに追加します。  
  
10. もう一方のパネルにはパネルから円コントロールをドラッグし、CTRL キーを押しながらにドロップします。 円がコピーされ、コピーに追加されます、<xref:System.Windows.Controls.Panel.Children%2A>受信側のパネルのコレクション。  
  
     ![CTRL キーを押しながら Circle をドラッグ](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")  
  
## <a name="see-also"></a>参照  
 [ドラッグ アンド ドロップの概要](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
