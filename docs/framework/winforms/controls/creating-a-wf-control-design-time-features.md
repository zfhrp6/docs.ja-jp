---
title: "チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成 | Microsoft Docs"
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
  - "デザイン時機能, Windows フォーム"
  - "DocumentDesigner クラス [Windows フォーム]"
  - "チュートリアル [Windows フォーム], コントロール"
  - "Windows フォーム コントロール, 作成"
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
caps.latest.revision: 46
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 46
---
# チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成
カスタム コントロールのデザイン時の操作性は、関連付けられたカスタム デザイナーを作成することで向上させることができます。  
  
 このチュートリアルでは、カスタム コントロールのカスタム デザイナーを作成する方法について説明します。  ここでは、`MarqueeControl` 型と、それに関連付けられた `MarqueeControlRootDesigner` というデザイナー クラスを実装します。  
  
 `MarqueeControl` 型は、光のアニメーションを表示し、テキストが点滅する、劇場の看板のようなディスプレイを実装します。  
  
 このコントロールのデザイナーは、デザイン環境と対話して、独自のデザイン時操作を提供します。  カスタム デザイナーを使用すると、光のアニメーションと点滅するテキストを多彩に組み合わせたカスタム `MarqueeControl` 実装をアセンブルできます。  アセンブルされたコントロールは、他の Windows フォーム コントロールと同じようにフォーム上で使用できます。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成  
  
-   コントロール ライブラリ プロジェクトの作成  
  
-   カスタム コントロール プロジェクトの参照  
  
-   カスタム コントロールとそのカスタム デザイナーの定義  
  
-   カスタム コントロールのインスタンスの作成  
  
-   デザイン時デバッグのためのプロジェクト設定  
  
-   カスタム コントロールの実装  
  
-   カスタム コントロールの子コントロールの作成  
  
-   MarqueeBorder の子コントロールの作成  
  
-   プロパティをシャドウおよびフィルター処理するカスタム デザイナーの作成  
  
-   コンポーネントの変更処理  
  
-   カスタム デザイナーへのデザイナー動詞の追加  
  
-   カスタム UITypeEditor の作成  
  
-   デザイナーでのカスタム コントロールのテスト  
  
 完成したカスタム コントロールは次のようになります。  
  
 ![可能な MarqueeControl 配置](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")  
  
 完全なコードの一覧については、「[How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Visual Studio がインストールされているコンピューターで、Windows フォーム アプリケーション プロジェクトを作成および実行するための十分なアクセス許可が付与されていること。  
  
## プロジェクトの作成  
 最初にアプリケーション プロジェクトを作成します。  このプロジェクトを使用して、カスタム コントロールをホストするアプリケーションをビルドします。  
  
#### プロジェクトを作成するには  
  
-   "MarqueeControlTest" という名前の Windows フォーム アプリケーション プロジェクトを作成します。詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
## コントロール ライブラリ プロジェクトの作成  
 次に、コントロール ライブラリ プロジェクトを作成します。  新しいカスタム コントロールとそれに対応するカスタム デザイナーを作成します。  
  
#### コントロール ライブラリ プロジェクトを作成するには  
  
1.  Windows フォーム コントロール ライブラリ プロジェクトをソリューションに追加します。  プロジェクトに "MarqueeControlLibrary" という名前を付けます。  
  
2.  **ソリューション エクスプローラー**を使用して、選択した言語に応じて "UserControl1.cs" または "UserControl1.vb" という名前のソース ファイルを削除して、プロジェクトの既定のコントロールを削除します。  詳細については、「[NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/ja-jp/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)」を参照してください。  
  
3.  新しい <xref:System.Windows.Forms.UserControl> アイテムを `MarqueeControlLibrary` プロジェクトに追加します。  新しいソース ファイルに、"MarqueeControl" という基本名を付けます。  
  
4.  **ソリューション エクスプローラー**を使用して、`MarqueeControlLibrary` プロジェクト内に新しいフォルダーを作成します。  詳細については、「[NIB:How to: Add New Project Items](http://msdn.microsoft.com/ja-jp/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)」を参照してください。  新しいフォルダーに "Design" という名前を付けます。  
  
5.  **Design** フォルダーを右クリックして、新しいクラスを追加します。  ソース ファイルに、"MarqueeControlRootDesigner" という基本名を付けます。  
  
6.  System.Design アセンブリの型を使用して、この参照を `MarqueeControlLibrary` プロジェクトに追加する必要があります。  
  
    > [!NOTE]
    >  System.Design アセンブリを使用するには、.NET Framework Client Profile ではなく、.NET Framework の完全バージョンをプロジェクトで対象とする必要があります。  ターゲット フレームワークを変更する方法については、「[方法: .NET Framework のバージョンをターゲットにする](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)」を参照してください。  
  
## カスタム コントロール プロジェクトの参照  
 `MarqueeControlTest` プロジェクトを使用して、カスタム コントロールをテストします。  テスト プロジェクトは、`MarqueeControlLibrary` アセンブリにプロジェクト参照を追加すると、カスタム コントロールを認識します。  
  
#### カスタム コントロール プロジェクトを参照するには  
  
-   `MarqueeControlTest` プロジェクトで、プロジェクト参照を `MarqueeControlLibrary` アセンブリに追加します。  `MarqueeControlLibrary` アセンブリを直接参照する代わりに、必ず、**\[参照の追加\]** ダイアログ ボックスの **\[プロジェクト\]** タブを使用してください。  
  
## カスタム コントロールとそのカスタム デザイナーの定義  
 カスタム コントロールは、<xref:System.Windows.Forms.UserControl> クラスから派生します。  これにより、カスタム コントロールに他のコントロールを含めることができ、既定の機能を豊富に割り当てることができます。  
  
 カスタム コントロールには、カスタム デザイナーが関連付けられます。  これにより、カスタム コントロールに特化された、独自のデザイン操作を実現できます。  
  
 カスタム コントロールをデザイナーに関連付けるには、<xref:System.ComponentModel.DesignerAttribute> クラスを使用します。  カスタム コントロールのデザイン時動作全体を開発するため、カスタム デザイナーは <xref:System.ComponentModel.Design.IRootDesigner> インターフェイスを実装します。  
  
#### カスタム コントロールとそのカスタム デザイナーを定義するには  
  
1.  `MarqueeControl` ソース ファイルを**コード エディター**で開きます。  ファイルの先頭に次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  <xref:System.ComponentModel.DesignerAttribute> を `MarqueeControl` クラス宣言に追加します。  これで、カスタム コントロールがデザイナーに関連付けられます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  `MarqueeControlRootDesigner` ソース ファイルを**コード エディター**で開きます。  ファイルの先頭に次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  <xref:System.Windows.Forms.Design.DocumentDesigner> クラスを継承するように `MarqueeControlRootDesigner` の宣言を変更します。  <xref:System.ComponentModel.ToolboxItemFilterAttribute> を適用して、デザイナーと**ツールボックス**との対話処理を指定します。  
  
     **メモ** `MarqueeControlRootDesigner` クラスの定義を、"MarqueeControlLibrary.Design" という名前空間に含めます。この宣言により、デザイン関連型用に予約されている特別な名前空間にデザイナーが配置されます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  `MarqueeControlRootDesigner` クラスのコンストラクターを定義します。  <xref:System.Diagnostics.Trace.WriteLine%2A> ステートメントをコンストラクター本体に挿入します。  これはデバッグに役立ちます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## カスタム コントロールのインスタンスの作成  
 コントロールのデザイン時のカスタム動作を確認するために、コントロールのインスタンスを `MarqueeControlTest` プロジェクトのフォームに配置します。  
  
#### カスタム コントロールのインスタンスを作成するには  
  
1.  新しい <xref:System.Windows.Forms.UserControl> アイテムを `MarqueeControlTest` プロジェクトに追加します。  新しいソース ファイルに、"DemoMarqueeControl" という基本名を付けます。  
  
2.  `DemoMarqueeControl` ファイルを**コード エディター**で開きます。  ファイルの先頭に、次のように `MarqueeControlLibrary` 名前空間をインポートします。  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  `MarqueeControl` クラスを継承するように `DemoMarqueeControl` の宣言を変更します。  
  
2.  プロジェクトをビルドします。  
  
3.  Windows フォーム デザイナーで `Form1` を開きます。  
  
4.  **ツールボックス**の **\[MarqueeControlTest コンポーネント\]** タブを見つけて開きます。  **ツールボックス**の `DemoMarqueeControl` コントロールをフォームにドラッグします。  
  
5.  プロジェクトをビルドします。  
  
## デザイン時デバッグのためのプロジェクト設定  
 デザイン時のカスタム操作を開発するときは、コントロールとコンポーネントのデバッグが必要になります。  プロジェクトでは、簡単な方法でデザイン時のデバッグを有効に設定できます。  詳細については、「[チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)」を参照してください。  
  
#### デザイン時デバッグのためにプロジェクトを設定するには  
  
1.  `MarqueeControlLibrary` プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  \[MarqueeControlLibrary プロパティ ページ\] ダイアログ ボックスで、**\[デバッグ\]** ページを選択します。  
  
3.  **\[開始動作\]** セクションで、**\[外部プログラムの開始\]** を選択します。  Visual Studio の別個のインスタンスをデバッグするので、省略記号 \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックして、Visual Studio IDE を参照します。  実行可能ファイルの名前は devenv.exe で、既定の場所にインストールした場合、ファイルのパスは "%programfiles%\\Microsoft Visual Studio 9.0\\Common7\\IDE\\devenv.exe" になります。  
  
4.  \[OK\] をクリックし、ダイアログ ボックスを閉じます。  
  
5.  `MarqueeControlLibrary` プロジェクトを右クリックし、\[スタートアップ プロジェクトに設定\] をクリックして、このデバッグ構成を有効にします。  
  
## チェックポイント  
 これで、カスタム コントロールのデザイン時動作をデバッグできるようになりました。  デバッグ環境が適切に設定されていることを確認したら、カスタム コントロールとカスタム デザイナーの関連付けをテストします。  
  
#### デバッグ環境およびデザイナーとの関連付けをテストするには  
  
1.  **コード エディター**で `MarqueeControlRootDesigner` ソース ファイルを開き、<xref:System.Diagnostics.Trace.WriteLine%2A> ステートメントにブレークポイントを配置します。  
  
2.  F5 キーを押してデバッグ セッションを開始します。  Visual Studio の新しいインスタンスが作成されることを確認してください。  
  
3.  Visual Studio の新しいインスタンスで、"MarqueeControlTest" ソリューションを開きます。  **\[ファイル\]** メニューの **\[最近使ったプロジェクト\]** をクリックすると、ソリューションが簡単に見つかります。  "MarqueeControlTest.sln" ソリューション ファイルが、最後に使用したファイルとして表示されます。  
  
4.  デザイナーで `DemoMarqueeControl` を開きます。  Visual Studio のデバッグ インスタンスがフォーカスを取得し、ブレークポイントで実行が停止します。  F5 キーを押して、デバッグ セッションを継続します。  
  
 この時点で、カスタム コントロールとそれに関連付けられたカスタム デザイナーを開発し、デバッグする準備がすべて整いました。  このチュートリアルの残りの部分では、コントロールとデザイナーの機能の実装について詳しく説明します。  
  
## カスタム コントロールの実装  
 `MarqueeControl` は、わずかにカスタマイズされた <xref:System.Windows.Forms.UserControl> コントロールです。  このコントロールは、マーキー アニメーションを開始する `Start` と、アニメーションを停止する `Stop` の 2 つのメソッドを公開します。  `MarqueeControl` は、`IMarqueeWidget` インターフェイスを実装する子コントロールを含むため、`Start` と `Stop` は各子コントロールを列挙し、`IMarqueeWidget` を実装する子コントロールごとに `StartMarquee` メソッドと `StopMarquee` メソッドをそれぞれ呼び出します。  
  
 `MarqueeBorder` コントロールと `MarqueeText` コントロールの外観はレイアウトによって異なるため、`MarqueeControl` は <xref:System.Windows.Forms.Control.OnLayout%2A> メソッドをオーバーライドし、同じ型の子コントロールで <xref:System.Windows.Forms.Control.PerformLayout%2A> を呼び出します。  
  
 これが `MarqueeControl` のカスタマイズの範囲です。  実行時の機能は、`MarqueeBorder` コントロールと `MarqueeText` コントロールによって実装され、デザイン時の機能は、`MarqueeBorderDesigner` クラスと `MarqueeControlRootDesigner` クラスによって実装されます。  
  
#### カスタム コントロールを実装するには  
  
1.  `MarqueeControl` ソース ファイルを**コード エディター**で開きます。  `Start` メソッドと `Stop` メソッドを実装します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  <xref:System.Windows.Forms.Control.OnLayout%2A> メソッドをオーバーライドします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## カスタム コントロールの子コントロールの作成  
 `MarqueeControl` は、`MarqueeBorder` コントロールと `MarqueeText` コントロールという 2 種類の子コントロールをホストします。  
  
-   `MarqueeBorder`: このコントロールは、その端に "光" の境界線を描画します。  光は連続して点滅するため、境界線を移動するように見えます。  光の点滅速度は、`UpdatePeriod` というプロパティで制御します。  コントロールのその他の外観は、これ以外のいくつかのカスタム プロパティによって設定します。  アニメーションの開始と停止は、`StartMarquee` および `StopMarquee` という 2 つのメソッドで制御します。  
  
-   `MarqueeText`: このコントロールは、点滅する文字列を描画します。  テキストの点滅速度は、`MarqueeBorder` コントロールと同様に `UpdatePeriod` プロパティで制御します。  また、`MarqueeText` コントロールには、`MarqueeBorder` コントロールと同様に `StartMarquee` メソッドと `StopMarquee` メソッドもあります。  
  
 デザイン時に `MarqueeControlRootDesigner` では、これら 2 種類のコントロールを自由に組み合わせて `MarqueeControl` に追加できます。  
  
 2 つのコントロールの共通機能は、`IMarqueeWidget` というインターフェイスに組み込まれます。  これにより、`MarqueeControl` が Marquee 関連の子コントロールを探索し、特別に処理できます。  
  
 周期的なアニメーション機能を実装するには、<xref:System.ComponentModel?displayProperty=fullName> 名前空間の <xref:System.ComponentModel.BackgroundWorker> オブジェクトを使用します。  <xref:System.Windows.Forms.Timer> オブジェクトを使用することもできますが、多くの `IMarqueeWidget` オブジェクトが存在するときは、単一の UI スレッドではアニメーションに対応できなくなることがあります。  
  
#### カスタム コントロールの子コントロールを作成するには  
  
1.  新しいクラス アイテムを `MarqueeControlLibrary` プロジェクトに追加します。  新しいソース ファイルに、"IMarqueeWidget" という基本名を付けます。  
  
2.  **コード エディター**で `IMarqueeWidget` ソース ファイルを開き、次のように `class` から `interface` に宣言を変更します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  次のコードを `IMarqueeWidget` インターフェイスに追加し、マーキー アニメーションを操作する 2 つのメソッドとプロパティを公開します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  新しい**カスタム コントロール** アイテムを `MarqueeControlLibrary` プロジェクトに追加します。  新しいソース ファイルに、"MarqueeText" という基本名を付けます。  
  
5.  **ツールボックス**の <xref:System.ComponentModel.BackgroundWorker> コンポーネントを `MarqueeText` コントロールにドラッグします。  このコンポーネントにより、`MarqueeText` コントロールが非同期的に更新されます。  
  
6.  \[プロパティ\] ウィンドウで、<xref:System.ComponentModel.BackgroundWorker> コンポーネントの `WorkerReportsProgess` プロパティと <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> プロパティを `true` に設定します。  これらの設定により、<xref:System.ComponentModel.BackgroundWorker> コンポーネントが周期的に <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントを発生させたり、非同期の更新をキャンセルしたりできます。  詳細については、「[BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)」を参照してください。  
  
7.  `MarqueeText` ソース ファイルを**コード エディター**で開きます。  ファイルの先頭に次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  `MarqueeText` の宣言を次のように変更し、<xref:System.Windows.Forms.Label> を継承すると共に、`IMarqueeWidget` インターフェイスを実装します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. 公開されたプロパティに対応するインスタンス変数を宣言し、コンストラクターで初期化します。  `isLit` フィールドで、`LightColor` プロパティで指定された色でテキストを描画するかどうかを指定します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. `IMarqueeWidget` インターフェイスを実装します。  
  
     `StartMarquee` メソッドと `StopMarquee` メソッドが、<xref:System.ComponentModel.BackgroundWorker> コンポーネントの <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> メソッドと <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> メソッドを呼び出して、アニメーションを開始および停止します。  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A> 属性と <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> 属性が `UpdatePeriod` プロパティに適用され、その結果、このプロパティが \[プロパティ\] ウィンドウの "Marquee" というカスタム セクションに表示されます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. プロパティのアクセサーを実装します。  `LightColor` と `DarkColor` という 2 つのプロパティをクライアントに公開します。  <xref:System.ComponentModel.CategoryAttribute.Category%2A> 属性と <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> 属性がこれらのプロパティに適用され、その結果、これらのプロパティが \[プロパティ\] ウィンドウの "Marquee" というカスタム セクションに表示されます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. <xref:System.ComponentModel.BackgroundWorker> コンポーネントの <xref:System.ComponentModel.BackgroundWorker.DoWork> イベントと <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントのハンドラーを実装します。  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーは、`UpdatePeriod` で指定したミリ秒数の間スリープした後、コードが <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> を呼び出してアニメーションを停止するまで <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントを発生させます。  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベント ハンドラーは、テキストを明るい状態と暗い状態の間で切り替えて、点滅しているように表示します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドして、アニメーションを有効にします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. F6 キーを押してソリューションをビルドします。  
  
## MarqueeBorder の子コントロールの作成  
 `MarqueeBorder` コントロールは、`MarqueeText` コントロールよりもわずかに洗練されています。  このコントロールにはより多くのプロパティがあり、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドのアニメーションはより複雑になっています。  ただし、`MarqueeText` コントロールは基本的には MarqueeText コントロールと同じです。  
  
 `MarqueeBorder` コントロールは子コントロールを含むことができるので、<xref:System.Windows.Forms.Control.Layout> イベントを認識する必要があります。  
  
#### MarqueeBorder コントロールを作成するには  
  
1.  新しい**カスタム コントロール** アイテムを `MarqueeControlLibrary` プロジェクトに追加します。  新しいソース ファイルに、"MarqueeBorder" という基本名を付けます。  
  
2.  **ツールボックス**から <xref:System.ComponentModel.BackgroundWorker> コンポーネントを `MarqueeBorder` コントロールにドラッグします。  このコンポーネントにより、`MarqueeBorder` コントロールが非同期的に更新されます。  
  
3.  \[プロパティ\] ウィンドウで、<xref:System.ComponentModel.BackgroundWorker> コンポーネントの `WorkerReportsProgess` プロパティと <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> プロパティを `true` に設定します。  これらの設定により、<xref:System.ComponentModel.BackgroundWorker> コンポーネントが周期的に <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントを発生させたり、非同期の更新をキャンセルしたりできます。  詳細については、「[BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)」を参照してください。  
  
4.  \[プロパティ\] ウィンドウの \[イベント\] をクリックします。  <xref:System.ComponentModel.BackgroundWorker.DoWork> イベントと <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントのハンドラーをアタッチします。  
  
5.  `MarqueeBorder` ソース ファイルを**コード エディター**で開きます。  ファイルの先頭に次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  `MarqueeBorder` の宣言を次のように変更し、<xref:System.Windows.Forms.Panel> を継承すると共に、`IMarqueeWidget` インターフェイスを実装します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  `MarqueeBorder` コントロールの状態を管理する `MarqueeSpinDirection` と `MarqueeLightShape` の 2 つの列挙型を宣言します。前者は、光が境界線を "回る" 方向を指定し、後者は、光の形状 \(四角形または円形\) を指定します。  これらの宣言を、`MarqueeBorder` クラス宣言の前に配置します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  公開されたプロパティに対応するインスタンス変数を宣言し、コンストラクターで初期化します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. `IMarqueeWidget` インターフェイスを実装します。  
  
     `StartMarquee` メソッドと `StopMarquee` メソッドが、<xref:System.ComponentModel.BackgroundWorker> コンポーネントの <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> メソッドと <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> メソッドを呼び出して、アニメーションを開始および停止します。  
  
     `MarqueeBorder` コントロールは子コントロールを含むことができるので、`StartMarquee` メソッドは、すべての子コントロールを列挙し、`IMarqueeWidget` を実装する子コントロールで `StartMarquee` を呼び出します。  `StopMarquee` メソッドも同じような実装になります。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. プロパティのアクセサーを実装します。  `MarqueeBorder` コントロールには、その外観を制御するプロパティがいくつかあります。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. <xref:System.ComponentModel.BackgroundWorker> コンポーネントの <xref:System.ComponentModel.BackgroundWorker.DoWork> イベントと <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントのハンドラーを実装します。  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーは、`UpdatePeriod` で指定したミリ秒数の間スリープした後、コードが <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> を呼び出してアニメーションを停止するまで <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントを発生させます。  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベント ハンドラーは、他の光の明暗の状態を決定するための基準になる "基本" 光の位置をインクリメントし、<xref:System.Windows.Forms.Control.Refresh%2A> メソッドを呼び出して、コントロール自体を再描画させます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. `IsLit` ヘルパー メソッドと `DrawLight` ヘルパー メソッドを実装します。  
  
     `IsLit` メソッドは、特定の位置での光の色を指定します。  "点灯中" の光は、`LightColor` プロパティで指定された色で描画され、"暗い" 光は、`DarkColor` プロパティで指定された色で描画されます。  
  
     `DrawLight` メソッドは、適切な色、形状、および位置を使用して光を描画します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. <xref:System.Windows.Forms.Control.OnLayout%2A> メソッドと <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドします。  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドは、`MarqueeBorder` コントロールの端に沿って光を描画します。  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドは、`MarqueeBorder` コントロールの寸法に依存するため、レイアウトを変更したときには必ず呼び出す必要があります。  このために、<xref:System.Windows.Forms.Control.OnLayout%2A> をオーバーライドして、<xref:System.Windows.Forms.Control.Refresh%2A> を呼び出します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## プロパティをシャドウおよびフィルター処理するカスタム デザイナーの作成  
 `MarqueeControlRootDesigner` クラスは、ルート デザイナーの実装を提供します。  `MarqueeControl` で動作するこのデザイナーに加えて、`MarqueeBorder` コントロールに特別に関連付けられたカスタム デザイナーも必要です。  このカスタム デザイナーは、カスタム ルート デザイナーのコンテキストに応じたカスタム動作を実現します。  
  
 具体的には、`MarqueeBorderDesigner` は、`MarqueeBorder` コントロールの特定のプロパティを "シャドウ" およびフィルター処理して、デザイン環境との対話方法を変更します。  
  
 コンポーネントのプロパティ アクセサーの呼び出しを受け取ることを "シャドウ" と言います。これにより、ユーザーによって設定された値をデザイナーが追跡でき、デザインされるコンポーネントにその値を渡すこともできます。  
  
 たとえば、<xref:System.Windows.Forms.Control.Visible%2A> プロパティと <xref:System.Windows.Forms.Control.Enabled%2A> プロパティを `MarqueeBorderDesigner` で Shadows' を実行すると、デザイン時にユーザーが `MarqueeBorder` コントロールを非表示にしたり、無効にしたりできなくなります。  
  
 また、デザイナーはプロパティを追加したり削除したりできます。  たとえば、`MarqueeBorder` コントロールでは、`LightSize` プロパティで指定された光のサイズに基づいて埋め込みがプログラムによって設定されるため、デザイン時に <xref:System.Windows.Forms.Control.Padding%2A> プロパティが削除されます。  
  
 `MarqueeBorderDesigner` の基本クラスは <xref:System.ComponentModel.Design.ComponentDesigner> で、デザイン時にコントロールによって公開される属性、プロパティ、およびイベントを変更できる以下のメソッドがあります。  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 これらのメソッドを使用してコンポーネントのパブリック インターフェイスを変更するときは、次の規則に従う必要があります。  
  
-   `PreFilter` メソッドのみで、アイテムを追加または削除します。  
  
-   `PostFilter` メソッドのみで、既存のアイテムを変更します。  
  
-   `PreFilter` メソッドでは、必ず最初に基本実装を呼び出します。  
  
-   `PostFilter` メソッドでは、必ず最後に基本実装を呼び出します。  
  
 これらの規則に従うことにより、デザイン時環境のすべてのデザイナーが、デザインされるすべてのコンポーネントで一貫したビューを持つことができます。  
  
 <xref:System.ComponentModel.Design.ComponentDesigner> クラスは、Shadows' を実行されたプロパティの値を管理するためのディクショナリを提供するため、特定のインスタンス変数を作成する必要がありません。  
  
#### プロパティをシャドウおよびフィルター処理するカスタム デザイナーを作成するには  
  
1.  **Design** フォルダーを右クリックして、新しいクラスを追加します。  ソース ファイルに、"MarqueeBorderDesigner" という基本名を付けます。  
  
2.  `MarqueeBorderDesigner` ソース ファイルを**コード エディター**で開きます。  ファイルの先頭に次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  <xref:System.Windows.Forms.Design.ParentControlDesigner> を継承するように `MarqueeBorderDesigner` の宣言を変更します。  
  
     `MarqueeBorder` コントロールは子コントロールを含むことができるので、`MarqueeBorderDesigner` は、親子の対話を処理する <xref:System.Windows.Forms.Design.ParentControlDesigner> を継承します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A> の基本実装をオーバーライドします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  <xref:System.Windows.Forms.Control.Enabled%2A> プロパティと <xref:System.Windows.Forms.Control.Visible%2A> プロパティを実装します。  これらの実装によってコントロールのプロパティがシャドウされます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## コンポーネントの変更処理  
 `MarqueeControlRootDesigner` クラスは、`MarqueeControl` インスタンスのデザイン時のカスタム操作を提供します。  デザイン時機能のほとんどが <xref:System.Windows.Forms.Design.DocumentDesigner> クラスから継承されるので、コンポーネントの変更処理とデザイナー動詞の追加という 2 つの固有のカスタマイズをコードで実装します。  
  
 ユーザーが各自の `MarqueeControl` インスタンスをデザインするときに、ルート デザイナーは、`MarqueeControl` とその子コントロールに対する変更を追跡します。  デザイン時環境は、コンポーネント状態の変更を追跡するための <xref:System.ComponentModel.Design.IComponentChangeService> という便利なサービスを提供します。  
  
 このサービスへの参照を取得するには、<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> メソッドを使用してデザイン時環境を照会します。  照会が成功すると、デザイナーは、<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> イベントのハンドラーをアタッチし、デザイン時に一貫した状態を保持する上で必要なタスクを実行できます。  
  
 `MarqueeControlRootDesigner` クラスの場合は、`MarqueeControl` に含まれている各 `IMarqueeWidget` オブジェクトで <xref:System.Windows.Forms.Control.Refresh%2A> メソッドを呼び出します。  これにより、親の <xref:System.Windows.Forms.Control.Size%2A> などのプロパティが変更されたときに `IMarqueeWidget` オブジェクト自体が適切に再描画されます。  
  
#### コンポーネントの変更を処理するには  
  
1.  **コード エディター**で `MarqueeControlRootDesigner` ソース ファイルを開き、<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> メソッドをオーバーライドします。  <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> の基本実装を呼び出し、<xref:System.ComponentModel.Design.IComponentChangeService> を照会します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> イベント ハンドラーを実装します。  送信側のコンポーネントの型をテストし、それが `IMarqueeWidget` の場合は、その <xref:System.Windows.Forms.Control.Refresh%2A> メソッドを呼び出します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## カスタム デザイナーへのデザイナー動詞の追加  
 デザイナー動詞は、イベント ハンドラーにリンクされたメニュー コマンドです。  デザイナー動詞は、デザイン時にコンポーネントのショートカット メニューに追加されます。  詳細については、「<xref:System.ComponentModel.Design.DesignerVerb>」を参照してください。  
  
 **\[テストの実行\]** と **\[テストの停止\]** の 2 つのデザイナー動詞をデザイナーに追加します。  これらの動詞を使用すると、`MarqueeControl` の実行時の動作をデザイン時に確認できます。  これらの動詞は、`MarqueeControlRootDesigner` に追加されます。  
  
 **\[テストの実行\]** を起動すると、動詞イベント ハンドラーが `MarqueeControl` で `StartMarquee` メソッドを呼び出します。  また、**\[テストの停止\]** を起動すると、動詞イベント ハンドラーが `MarqueeControl` で `StopMarquee` メソッドを呼び出します。  `StartMarquee` メソッドと `StopMarquee` メソッドの実装は、`IMarqueeWidget` を実装する、包含される側のコントロールでこれらのメソッドを呼び出すため、包含される `IMarqueeWidget` コントロールもすべてテストに加わります。  
  
#### デザイナー動詞をカスタム デザイナーに追加するには  
  
1.  `MarqueeControlRootDesigner` クラスに、`OnVerbRunTest` および `OnVerbStopTest` という名前のイベント ハンドラーを追加します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  これらのイベント ハンドラーを、対応するデザイナー動詞に接続します。  `MarqueeControlRootDesigner` は、基本クラスから <xref:System.ComponentModel.Design.DesignerVerbCollection> を継承します。  新たに 2 つの <xref:System.ComponentModel.Design.DesignerVerb> オブジェクトを作成し、<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> メソッドのこのコレクションに追加します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## カスタム UITypeEditor の作成  
 ユーザーに対しデザイン時のカスタム操作を作成するときは、一般に \[プロパティ\] ウィンドウを使用してカスタム対話を作成することが望まれます。  これを行うには、<xref:System.Drawing.Design.UITypeEditor> を作成します。  詳細については、「[How to: Create a UI Type Editor](../Topic/How%20to:%20Create%20a%20UI%20Type%20Editor.md)」を参照してください。  
  
 `MarqueeBorder` コントロールは、\[プロパティ\] ウィンドウにいくつかのプロパティを公開します。  これらのプロパティのうち、`MarqueeSpinDirection` と `MarqueeLightShape` の 2 つは列挙型で表されます。  UI 型エディターの使い方を示すために、`MarqueeLightShape` プロパティには、<xref:System.Drawing.Design.UITypeEditor> クラスが関連付けられます。  
  
#### カスタム UI 型エディターを作成するには  
  
1.  `MarqueeBorder` ソース ファイルを**コード エディター**で開きます。  
  
2.  `MarqueeBorder` クラスの定義で、<xref:System.Drawing.Design.UITypeEditor> から派生する、`LightShapeEditor` という名前のクラスを宣言します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  `editorService` という <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> インスタンス変数を宣言します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> メソッドをオーバーライドします。  この実装は、`LightShapeEditor` の表示方法をデザイン環境に指示する <xref:System.Drawing.Design.UITypeEditorEditStyle> を返します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> メソッドをオーバーライドします。  この実装は、デザイン環境に <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> オブジェクトを照会します。  照会が成功すると、`LightShapeSelectionControl` が作成されます。  <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> メソッドを呼び出して、`LightShapeEditor` を起動します。  この呼び出しの戻り値がデザイン環境に返されます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## カスタム UITypeEditor のビュー コントロールの作成  
  
1.  `MarqueeLightShape` プロパティは、`Square` と `Circle` の 2 種類の光の形状をサポートします。  ここでは、これらの値を \[プロパティ\] ウィンドウにグラフィカルに表示するためだけに使用するカスタム コントロールを作成します。  このカスタム コントロールは、<xref:System.Drawing.Design.UITypeEditor> が \[プロパティ\] ウィンドウと対話するために使用します。  
  
#### カスタム UI 型エディターのビュー コントロールを作成するには  
  
1.  新しい <xref:System.Windows.Forms.UserControl> アイテムを `MarqueeControlLibrary` プロジェクトに追加します。  新しいソース ファイルに、"LightShapeSelectionControl" という基本名を付けます。  
  
2.  **\[ツールボックス\]** から 2 つの <xref:System.Windows.Forms.Panel> コントロールを `LightShapeSelectionControl` にドラッグします。  これらのコントロールに `squarePanel` および `circlePanel` という名前を付けます。  これらを左右に並べて配置します。  両方の <xref:System.Windows.Forms.Panel> コントロールの <xref:System.Windows.Forms.Control.Size%2A> プロパティを \(60, 60\) に設定します。  `squarePanel` コントロールの <xref:System.Windows.Forms.Control.Location%2A> プロパティを \(8, 10\) に設定します。  `circlePanel` コントロールの <xref:System.Windows.Forms.Control.Location%2A> プロパティを \(80, 10\) に設定します。  最後に、`LightShapeSelectionControl` の <xref:System.Windows.Forms.Control.Size%2A> プロパティを \(150, 80\) に設定します。  
  
3.  `LightShapeSelectionControl` ソース ファイルを**コード エディター**で開きます。  ファイルの先頭に、次のように <xref:System.Windows.Forms.Design?displayProperty=fullName> 名前空間をインポートします。  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  `squarePanel` コントロールおよび `circlePanel` コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを実装します。  これらのメソッドは <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> を呼び出して、カスタム <xref:System.Drawing.Design.UITypeEditor> 編集セッションを終了させます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  `editorService` という <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> インスタンス変数を宣言します。  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  `lightShapeValue` という `MarqueeLightShape` インスタンス変数を宣言します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  `LightShapeSelectionControl` コンストラクターで、`squarePanel` コントロールと `circlePanel` コントロールの <xref:System.Windows.Forms.Control.Click> イベントに <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを追加します。  また、デザイン環境から `lightShapeValue` フィールドに `MarqueeLightShape` 値を割り当てる、コンストラクター オーバーロードを定義します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  <xref:System.ComponentModel.Component.Dispose%2A> メソッドで、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーをデタッチします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  **ソリューション エクスプローラー**の **\[すべてのファイルを表示\]** をクリックします。  LightShapeSelectionControl.Designer.cs ファイルまたは LightShapeSelectionControl.Designer.vb ファイルを開いて、<xref:System.ComponentModel.Component.Dispose%2A> メソッドの既定の定義を削除します。  
  
5.  `LightShape` プロパティを実装します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドします。  この実装によって、塗りつぶされた正方形と円が描画されます。  また、いずれかの図形の周囲に境界線を描画して、選択した値を強調表示します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## デザイナーでのカスタム コントロールのテスト  
 この時点で、`MarqueeControlLibrary` プロジェクトをビルドできます。  `MarqueeControl` クラスから継承するコントロールを作成し、それをフォームで使用して、実装をテストします。  
  
#### カスタム MarqueeControl 実装を作成するには  
  
1.  Windows フォーム デザイナーで `DemoMarqueeControl` を開きます。  これにより、`DemoMarqueeControl` 型のインスタンスが作成され、`MarqueeControlRootDesigner` 型のインスタンス内に表示されます。  
  
2.  **ツールボックス**の **\[MarqueeControlLibrary コンポーネント\]** タブを開きます。  `MarqueeBorder` コントロールと `MarqueeText` コントロールが選択可能なアイテムとして表示されます。  
  
3.  `MarqueeBorder` コントロールのインスタンスを `DemoMarqueeControl` のデザイン サーフェイスにドラッグします。  この `MarqueeBorder` コントロールを親コントロールにドッキングします。  
  
4.  `MarqueeText` コントロールのインスタンスを `DemoMarqueeControl` のデザイン サーフェイスにドラッグします。  
  
5.  ソリューションをビルドします。  
  
6.  `DemoMarqueeControl` を右クリックし、ショートカット メニューの **\[テストの実行\]** を選択すると、アニメーションが開始されます。  **\[テストの停止\]** をクリックして、アニメーションを停止します。  
  
7.  デザイン ビューで **\[Form1\]** を開きます。  
  
8.  2 つの <xref:System.Windows.Forms.Button> コントロールをフォームに配置します。  それらのコントロールに `startButton` および `stopButton` という名前を付け、<xref:System.Windows.Forms.Control.Text%2A> プロパティ値をそれぞれ「Start」と「Stop」に変更します。  
  
9. 両方の <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを実装します。  
  
10. **ツールボックス**の **\[MarqueeControlTest コンポーネント\]** タブを開きます。  `DemoMarqueeControl` が選択可能なアイテムとして表示されます。  
  
11. `DemoMarqueeControl` のインスタンスを **Form1** のデザイン サーフェイスにドラッグします。  
  
12. <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで、`DemoMarqueeControl` の `Start` メソッドと `Stop` メソッドを呼び出します。  
  
```vb  
Private Sub startButton_Click(sender As Object, e As System.EventArgs)  
    Me.demoMarqueeControl1.Start()  
End Sub 'startButton_Click  
  
Private Sub stopButton_Click(sender As Object, e As System.EventArgs)  
Me.demoMarqueeControl1.Stop()  
End Sub 'stopButton_Click  
```  
  
```csharp  
private void startButton_Click(object sender, System.EventArgs e)  
{  
    this.demoMarqueeControl1.Start();  
}  
  
private void stopButton_Click(object sender, System.EventArgs e)  
{  
    this.demoMarqueeControl1.Stop();  
}  
```  
  
1.  `MarqueeControlTest` プロジェクトをスタートアップ プロジェクトとして設定し、実行します。  フォームに `DemoMarqueeControl` が表示されます。  **\[開始\]** ボタンをクリックしてアニメーションを開始します。  テキストが点滅し、光が境界線上を移動するように見えます。  
  
## 次の手順  
 `MarqueeControlLibrary` は、カスタム コントロールとそれに関連付けられたデザイナーの簡単な実装を示しています。  このサンプルは、以下の方法でより洗練されたものにできます。  
  
-   デザイナーで `DemoMarqueeControl` のプロパティ値を変更します。  さらに `MarqueBorder` コントロールを追加し、親インスタンス内でドッキングして、入れ子の状態にします。  `UpdatePeriod` プロパティと光関連プロパティでさまざまな設定を試みます。  
  
-   `IMarqueeWidget` の独自の実装を作成します。  たとえば、点滅する "ネオン サイン" や、複数のイメージを表示するアニメーション サインを作成することもできます。  
  
-   デザイン時の操作をさらにカスタマイズします。  <xref:System.Windows.Forms.Control.Enabled%2A> と <xref:System.Windows.Forms.Control.Visible%2A> よりも多くのプロパティをシャドウしたり、新しいプロパティを追加したりできます。  新しいデザイナー動詞を追加して、子コントロールのドッキングなどの共通タスクを簡素化します。  
  
-   `MarqueeControl` のライセンス処理を行います。  詳細については、「[方法 : コンポーネントおよびコントロールのライセンス処理を行う](../Topic/How%20to:%20License%20Components%20and%20Controls.md)」を参照してください。  
  
-   コントロールをシリアル化する方法と、コントロールのコードを生成する方法を制御します。  詳細については、「[動的なソース コードの生成とコンパイル](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.UserControl>   
 <xref:System.Windows.Forms.Design.ParentControlDesigner>   
 <xref:System.Windows.Forms.Design.DocumentDesigner>   
 <xref:System.ComponentModel.Design.IRootDesigner>   
 <xref:System.ComponentModel.Design.DesignerVerb>   
 <xref:System.Drawing.Design.UITypeEditor>   
 <xref:System.ComponentModel.BackgroundWorker>   
 [How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)   
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [Custom Designers](../Topic/Custom%20Designers.md)   
 [.NET Shape Library: A Sample Designer \(.NET 図形ライブラリ: サンプル デザイナー\)](http://windowsforms.net/articles/shapedesigner.aspx)