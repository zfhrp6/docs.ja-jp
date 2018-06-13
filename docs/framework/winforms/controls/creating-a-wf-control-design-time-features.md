---
title: 'チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
ms.openlocfilehash: 10905df76f2b638c10b14c1dd8c181b9652ea963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529741"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成
関連付けられているカスタム デザイナーを作成して、カスタム コントロールのデザイン時機能を拡張できます。  
  
 このチュートリアルでは、カスタム コントロールのカスタム デザイナーを作成する方法について説明します。 実装、`MarqueeControl`型およびと呼ばれる、関連付けられたデザイナー クラス`MarqueeControlRootDesigner`です。  
  
 `MarqueeControl`アニメーションと点滅しているテキストのシアター marquee ような表示を実装しています。  
  
 このコントロールのデザイナーは、カスタム デザイン時のエクスペリエンスを提供するデザイン環境とやり取りします。 カスタム デザイナーを使用するカスタムをアセンブルできます`MarqueeControl`アニメーションと多くの組み合わせで点滅しているテキストを使用して実装します。 アセンブルされたコントロールは、他の Windows フォーム コントロールと同様に、フォームを使用することができます。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成  
  
-   コントロール ライブラリ プロジェクトを作成します。  
  
-   カスタム コントロール プロジェクトを参照します。  
  
-   カスタム コントロールとそのカスタム デザイナーを定義します。  
  
-   カスタム コントロールのインスタンスを作成します。  
  
-   デザイン時デバッグのためのプロジェクトの設定  
  
-   カスタム コントロールの実装  
  
-   カスタム コントロールの子コントロールの作成  
  
-   MarqueeBorder 子コントロールを作成します。  
  
-   シャドウとフィルターのプロパティにカスタム デザイナーを作成します。  
  
-   コンポーネントの変更の処理  
  
-   カスタム デザイナー動詞を追加します。  
  
-   カスタム  
  
-   デザイナーでカスタム コントロールのテスト  
  
 完了したら、カスタム コントロールは、次のようになります。  
  
 ![可能な MarqueeControl 配置](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "により")  
  
 完全なコード リストを参照してください。[する方法:、Windows フォーム コントロールを受け取る利点のデザイン時機能の作成](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初の手順では、アプリケーション プロジェクトを作成します。 このプロジェクトを使用するカスタム コントロールをホストするアプリケーションをビルドします。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
-   「ためです」と呼ばれる Windows フォーム アプリケーション プロジェクトを作成します。 詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
## <a name="creating-a-control-library-project"></a>コントロール ライブラリ プロジェクトを作成します。  
 次の手順では、コントロール ライブラリ プロジェクトを作成します。 新しいカスタム コントロールとその対応するカスタム デザイナーを作成します。  
  
#### <a name="to-create-the-control-library-project"></a>コントロール ライブラリ プロジェクトを作成するには  
  
1.  Windows フォーム コントロール ライブラリ プロジェクトをソリューションに追加します。 プロジェクト「に」の名前します。  
  
2.  使用して**ソリューション エクスプ ローラー**、選択した言語に応じて"UserControl1.cs"または"UserControl1.vb"をという名前のソース ファイルを削除して、プロジェクトの既定のコントロールを削除します。 詳細については、次を参照してください。 [NIB: 方法:: 削除、削除、および項目の除外](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)です。  
  
3.  新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル"MarqueeControl"の基本の名前を付けます  
  
4.  使用して**ソリューション エクスプ ローラー**で新しいフォルダーを作成、`MarqueeControlLibrary`プロジェクト。 詳細については、次を参照してください。 [NIB: 方法: 新しいプロジェクト項目の追加](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)です。 新しいフォルダーの名前を""設計します。  
  
5.  右クリックし、**デザイン**フォルダーと、新しいクラスを追加します。 ソース ファイル「ここでします」の基本の名前を付けます  
  
6.  System.Design アセンブリから型を使用して、この参照を追加する必要があります、`MarqueeControlLibrary`プロジェクト。  
  
    > [!NOTE]
    >  System.Design アセンブリを使用するのには、プロジェクトは .NET Framework クライアント プロファイルではなく、.NET Framework の完全バージョンを対象する必要があります。 ターゲット フレームワークを変更するを参照してください。[する方法: .NET Framework のバージョンを対象に](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)です。  
  
## <a name="referencing-the-custom-control-project"></a>カスタム コントロール プロジェクトを参照します。  
 使用して、`MarqueeControlTest`プロジェクトにカスタム コントロールをテストします。 プロジェクト参照を追加すると、テスト プロジェクトにカスタム コントロールを認識なります、`MarqueeControlLibrary`アセンブリ。  
  
#### <a name="to-reference-the-custom-control-project"></a>カスタム コントロール プロジェクトを参照するには  
  
-   `MarqueeControlTest`プロジェクト、プロジェクト参照を追加、`MarqueeControlLibrary`アセンブリ。 使用してください、**プロジェクト** タブで、**参照の追加** ダイアログ ボックスを参照するのではなく、`MarqueeControlLibrary`直接アセンブリ。  
  
## <a name="defining-a-custom-control-and-its-custom-designer"></a>カスタム コントロールとそのカスタム デザイナーを定義します。  
 カスタム コントロールの継承元、<xref:System.Windows.Forms.UserControl>クラスです。 これにより、他のコントロールを格納する、制御でき、コントロールの既定の機能が大幅に向上できます。  
  
 カスタム コントロールは、関連するカスタム デザイナーがあります。 これにより、カスタム コントロールに特化した独自のデザイン エクスペリエンスを作成することができます。  
  
 使用して、コントロールをそのデザイナーを関連付ける、<xref:System.ComponentModel.DesignerAttribute>クラスです。 カスタム デザイナーの実装は、カスタム コントロールの全体のデザイン時の動作を開発しているため、<xref:System.ComponentModel.Design.IRootDesigner>インターフェイスです。  
  
#### <a name="to-define-a-custom-control-and-its-custom-designer"></a>カスタム コントロールとそのカスタム デザイナーを定義するには  
  
1.  開く、`MarqueeControl`内のソース ファイル、**コード エディター**です。 ファイルの上部には、次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  追加、<xref:System.ComponentModel.DesignerAttribute>を`MarqueeControl`クラス宣言します。 これは、そのデザイナーをカスタム コントロールを関連付けます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**です。 ファイルの上部には、次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  宣言を変更する`MarqueeControlRootDesigner`から継承する、<xref:System.Windows.Forms.Design.DocumentDesigner>クラスです。 適用、<xref:System.ComponentModel.ToolboxItemFilterAttribute>デザイナー対話方式を指定する、**ツールボックス**です。  
  
     **注**の定義、`MarqueeControlRootDesigner`クラスは、"MarqueeControlLibrary.Design"と呼ばれる名前空間で囲まれています。 この宣言にデザイナーが配置特別な名前空間型のデザインに関連するために予約されています。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  コンス トラクターを定義、`MarqueeControlRootDesigner`クラスです。 挿入、<xref:System.Diagnostics.Trace.WriteLine%2A>コンス トラクターの本体のステートメント。 これは、デバッグのために便利になります。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## <a name="creating-an-instance-of-your-custom-control"></a>カスタム コントロールのインスタンスを作成します。  
 フォームにコントロールのインスタンスを配置するカスタム コントロールのデザイン時動作を観察する`MarqueeControlTest`プロジェクト。  
  
#### <a name="to-create-an-instance-of-your-custom-control"></a>カスタム コントロールのインスタンスを作成するには  
  
1.  新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlTest`プロジェクト。 新しいソース ファイルの「により」ベースの名前を付けます  
  
2.  開く、`DemoMarqueeControl`ファイルで、**コード エディター**です。 ファイルの上部には、インポート、`MarqueeControlLibrary`名前空間。  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  宣言を変更する`DemoMarqueeControl`から継承する、`MarqueeControl`クラスです。  
  
2.  プロジェクトをビルドします。  
  
3.  Windows フォーム デザイナーで `Form1` を開きます。  
  
4.  検索、**ためコンポーネント** タブで、**ツールボックス**して開きます。 ドラッグ、`DemoMarqueeControl`から、**ツールボックス**フォーム上にします。  
  
5.  プロジェクトをビルドします。  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>デザイン時デバッグのためのプロジェクトの設定  
 カスタム デザイン時機能を開発する際は、コントロールとコンポーネントをデバッグする必要があります。 デザイン時デバッグを許可する、プロジェクトを設定する簡単な方法があります。 詳細については、次を参照してください。[チュートリアル: デザイン時にカスタム Windows フォーム コントロールをデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)です。  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>デザイン時デバッグ用のプロジェクトを設定するには  
  
1.  右クリックし、`MarqueeControlLibrary`プロジェクトし、選択**プロパティ**です。  
  
2.  "にプロパティ ページ ダイアログ ボックスで、選択、**デバッグ**ページ。  
  
3.  **開始動作**セクションで、**外部プログラムの開始**です。 できます、省略記号ボタンをクリックして、Visual Studio の別のインスタンスをデバッグ (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を Visual Studio IDE の参照ボタンをクリックします。 実行可能ファイルの名前は、devenv.exe され、パスが %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe は既定の場所にインストールした場合。  
  
4.  ダイアログ ボックスを閉じるには、[ok] をクリックします。  
  
5.  右クリックし、`MarqueeControlLibrary`プロジェクトし、「スタートアップ プロジェクトに」このデバッグ構成を有効にするを選択します。  
  
## <a name="checkpoint"></a>チェックポイント  
 カスタム コントロールのデザイン時動作をデバッグする準備が整いました。 デバッグ環境が正しく設定されているを確認した後は、カスタム コントロールとカスタム デザイナー間の関連付けをテストします。  
  
#### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>デバッグ環境と、デザイナーとの関連付けをテストするには  
  
1.  開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**にブレークポイントを配置し、<xref:System.Diagnostics.Trace.WriteLine%2A>ステートメントです。  
  
2.  F5 キーを押してデバッグ セッションを開始します。 Visual Studio の新しいインスタンスを作成することに注意してください。  
  
3.  Visual Studio の新しいインスタンスの「ため」ソリューションを開きます。 選択して、ソリューションを簡単に見つけることができます**最近使ったプロジェクト**から、**ファイル**メニュー。 最近使用したファイル、"MarqueeControlTest.sln"ソリューション ファイルが表示されます。  
  
4.  開く、`DemoMarqueeControl`デザイナーでします。 Visual Studio のデバッグのインスタンスがフォーカスを取得し、実行をブレークポイントで停止することに注意してください。 F5 キーを押してデバッグ セッションを続行します。  
  
 この時点では、カスタム コントロールおよびその関連するカスタム デザイナーを開発、デバッグするためにすべてがされます。 このチュートリアルの残りの部分は、コントロールと、デザイナーの機能の実装の詳細に集中されます。  
  
## <a name="implementing-your-custom-control"></a>カスタム コントロールの実装  
 `MarqueeControl`は、<xref:System.Windows.Forms.UserControl>カスタマイズのほんの少しです。 2 つのメソッドを公開: `Start`、marquee アニメーションを開始し、`Stop`アニメーションは停止します。 `MarqueeControl`を実装する子コントロールが含まれています、`IMarqueeWidget`インターフェイス、`Start`と`Stop`各子コントロールと呼び出しの列挙、`StartMarquee`と`StopMarquee`メソッド、それぞれ、各子コントロール上実装する`IMarqueeWidget`です。  
  
 外観、`MarqueeBorder`と`MarqueeText`コントロールは、レイアウトに依存するため、`MarqueeControl`よりも優先、<xref:System.Windows.Forms.Control.OnLayout%2A>メソッドと呼び出し<xref:System.Windows.Forms.Control.PerformLayout%2A>子コントロールをこの型のです。  
  
 これは、程度、`MarqueeControl`カスタマイズします。 によって実行時の機能が実装されている、`MarqueeBorder`と`MarqueeText`コントロール、およびデザイン時の機能によって実装される、`MarqueeBorderDesigner`と`MarqueeControlRootDesigner`クラスです。  
  
#### <a name="to-implement-your-custom-control"></a>カスタム コントロールを実装するには  
  
1.  開く、`MarqueeControl`内のソース ファイル、**コード エディター**です。 実装、`Start`と`Stop`メソッドです。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  <xref:System.Windows.Forms.Control.OnLayout%2A> メソッドをオーバーライドします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## <a name="creating-a-child-control-for-your-custom-control"></a>カスタム コントロールの子コントロールの作成  
 `MarqueeControl` 2 種類の子コントロールをホストする:`MarqueeBorder`コントロールと`MarqueeText`コントロール。  
  
-   `MarqueeBorder`: このコントロールは、"lights"の端の周りの境界線を描画します。 ライトは、境界線を移動するように表示されるように、シーケンスで点滅します。 ライトが点滅する速度がという名前のプロパティによって制御されます`UpdatePeriod`です。 その他のいくつかのカスタム プロパティは、コントロールの外観の他の側面を決定します。 2 つのメソッドと呼ばれる`StartMarquee`と`StopMarquee`、ときに、アニメーションの開始し、停止を制御します。  
  
-   `MarqueeText`: このコントロールは、点滅している文字列を描画します。 同様に、`MarqueeBorder`コントロール、テキストが点滅速度は、によって制御されます、`UpdatePeriod`プロパティです。 `MarqueeText`コントロールもあります、`StartMarquee`と`StopMarquee`と共通のメソッド、`MarqueeBorder`コントロール。  
  
 デザイン時に、`MarqueeControlRootDesigner`これら 2 つのコントロール型に追加することができます、`MarqueeControl`の任意の組み合わせ。  
  
 2 つのコントロールの共通機能を考慮と呼ばれるインターフェイス`IMarqueeWidget`です。 これにより、`MarqueeControl`を範囲に関連する子コントロールを検出し、特別な処理を付与します。  
  
 定期的なアニメーション機能を実装するには、使用<xref:System.ComponentModel.BackgroundWorker>オブジェクトから、<xref:System.ComponentModel?displayProperty=nameWithType>名前空間。 使って<xref:System.Windows.Forms.Timer>が、オブジェクトが多`IMarqueeWidget`オブジェクトが存在、1 つの UI スレッドがアニメーションしきれないことができません。  
  
#### <a name="to-create-a-child-control-for-your-custom-control"></a>カスタム コントロールの子コントロールを作成するには  
  
1.  項目の追加、新しいクラス、`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル"IMarqueeWidget"の基本の名前を付けます  
  
2.  開く、`IMarqueeWidget`内のソース ファイル、**コード エディター**から宣言を変更して`class`に`interface`:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  次のコードを追加、 `IMarqueeWidget` 2 つのメソッドと marquee アニメーションを操作するプロパティを公開するインターフェイス。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  新しい**カスタム コントロールの**項目を`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル「ただし」の基本の名前を付けます  
  
5.  ドラッグ、<xref:System.ComponentModel.BackgroundWorker>のコンポーネント、**ツールボックス**上に、`MarqueeText`コントロール。 このコンポーネントを許可するが、`MarqueeText`自体を非同期的に更新するコントロール。  
  
6.  [プロパティ] ウィンドウで、設定、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの`WorkerReportsProgess`と<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティを`true`です。 これらの設定により、<xref:System.ComponentModel.BackgroundWorker>を定期的に発生させるコンポーネント、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントと非同期更新をキャンセルします。 詳細については、次を参照してください。 [BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)です。  
  
7.  開く、`MarqueeText`内のソース ファイル、**コード エディター**です。 ファイルの上部には、次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  宣言を変更する`MarqueeText`から継承する<xref:System.Windows.Forms.Label>を実装して、`IMarqueeWidget`インターフェイス。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. 公開されたプロパティに対応するインスタンス変数を宣言し、コンス トラクターで初期化します。 `isLit`フィールドかどうかをテキストで指定された色で描画する、`LightColor`プロパティです。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. `IMarqueeWidget` インターフェイスを実装します。  
  
     `StartMarquee`と`StopMarquee`メソッドを呼び出し、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>と<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>メソッドを開始し、アニメーションを停止します。  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A>と<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>属性に適用されます、 `UpdatePeriod` 「範囲」と呼ばれる [プロパティ] ウィンドウのカスタム セクションに表示されるようにプロパティ  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. プロパティ アクセサーを実装します。 クライアントに 2 つのプロパティを公開する:`LightColor`と`DarkColor`です。 <xref:System.ComponentModel.CategoryAttribute.Category%2A>と<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>属性は、「範囲」と呼ばれる [プロパティ] ウィンドウのカスタムのセクションでプロパティが表示されるので、これらのプロパティに適用されます  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. ハンドラーを実装、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork>ミリ秒で指定された数のイベント ハンドラーがスリープ状態`UpdatePeriod`を生成し、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントを呼び出すことによって、コードがアニメーションを停止するまで<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>です。  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラーは、テキストの点滅の外観、明暗の状態を切り替えます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. 上書き、<xref:System.Windows.Forms.Control.OnPaint%2A>アニメーションを有効にするメソッド。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. F6 キーを押してソリューションをビルドします。  
  
## <a name="create-the-marqueeborder-child-control"></a>MarqueeBorder 子コントロールを作成します。  
 `MarqueeBorder`コントロールがやや高度な`MarqueeText`コントロール。 その他のプロパティとでのアニメーションがある、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは複雑です。 原則として、非常に似ていますが、`MarqueeText`コントロール。  
  
 `MarqueeBorder`コントロールで子コントロールを持つことができます、注意する必要がある<xref:System.Windows.Forms.Control.Layout>イベント。  
  
#### <a name="to-create-the-marqueeborder-control"></a>MarqueeBorder コントロールを作成するには  
  
1.  新しい**カスタム コントロールの**項目を`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル"MarqueeBorder"の基本の名前を付けます  
  
2.  ドラッグ、<xref:System.ComponentModel.BackgroundWorker>のコンポーネント、**ツールボックス**上に、`MarqueeBorder`コントロール。 このコンポーネントを許可するが、`MarqueeBorder`自体を非同期的に更新するコントロール。  
  
3.  [プロパティ] ウィンドウで、設定、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの`WorkerReportsProgess`と<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティを`true`です。 これらの設定により、<xref:System.ComponentModel.BackgroundWorker>を定期的に発生させるコンポーネント、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントと非同期更新をキャンセルします。 詳細については、次を参照してください。 [BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)です。  
  
4.  [プロパティ] ウィンドウで、イベント ボタンをクリックします。 ハンドラーのアタッチ、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。  
  
5.  開く、`MarqueeBorder`内のソース ファイル、**コード エディター**です。 ファイルの上部には、次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  宣言を変更する`MarqueeBorder`から継承する<xref:System.Windows.Forms.Panel>を実装して、`IMarqueeWidget`インターフェイスです。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  管理するための 2 つの列挙型を宣言、`MarqueeBorder`コントロールの状態:`MarqueeSpinDirection`をライト""を中心として回転、境界線の方向を決めると`MarqueeLightShape`、(四角形または循環) のライトの形状を決定します。 配置する前にこれらの宣言、`MarqueeBorder`クラス宣言します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  公開されたプロパティに対応するインスタンス変数を宣言し、コンス トラクターで初期化します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. `IMarqueeWidget` インターフェイスを実装します。  
  
     `StartMarquee`と`StopMarquee`メソッドを呼び出し、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>と<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>メソッドを開始し、アニメーションを停止します。  
  
     `MarqueeBorder`コントロールで子コントロールを含めることができます、`StartMarquee`メソッドは、すべての子コントロールと呼び出しを列挙します。`StartMarquee`を実装するもので`IMarqueeWidget`です。 `StopMarquee`メソッドのような実装があります。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. プロパティ アクセサーを実装します。 `MarqueeBorder`コントロールの外観を制御するためのいくつかのプロパティがあります。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. ハンドラーを実装、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork>ミリ秒で指定された数のイベント ハンドラーがスリープ状態`UpdatePeriod`を生成し、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントを呼び出すことによって、コードがアニメーションを停止するまで<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>です。  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラーは、"base"、元は、他のライトの明/暗状態を判断、淡色テーマと呼び出しの位置をインクリメント、<xref:System.Windows.Forms.Control.Refresh%2A>メソッドを呼び出すと、コントロールを再描画します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. ヘルパー メソッドを実装する`IsLit`と`DrawLight`です。  
  
     `IsLit`メソッドは、指定した位置にある光の色を決定します。 によって指定された色で描画されます「が点灯している」ライト、`LightColor`プロパティ、および [ダーク] にあるものがで指定された色で描画された、`DarkColor`プロパティです。  
  
     `DrawLight`メソッドは適切な色、形状、および位置を使用して、ライトを描画します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. 上書き、<xref:System.Windows.Forms.Control.OnLayout%2A>と<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは、描画の端に沿ってライト、`MarqueeBorder`コントロール。  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの大きさによって異なります、`MarqueeBorder`コントロール、レイアウトが変更されたときに呼び出す必要があります。 そのため、オーバーライド<xref:System.Windows.Forms.Control.OnLayout%2A>を呼び出すと<xref:System.Windows.Forms.Control.Refresh%2A>です。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>シャドウとフィルターのプロパティにカスタム デザイナーを作成します。  
 `MarqueeControlRootDesigner`クラスがルート デザイナーの実装を提供します。 動作するこのデザイナーに加え、 `MarqueeControl`、具体的には関連付けられているカスタム デザイナーが必要になります、`MarqueeBorder`コントロール。 このデザイナーは、カスタム ルート デザイナーのコンテキストで適切なカスタム動作を提供します。  
  
 具体的には、 `MarqueeBorderDesigner` 「シャドウ」とに特定のプロパティをフィルター処理は、`MarqueeBorder`コントロール、デザイン環境との相互作用を変更します。  
  
 「シャドウ」と呼ばれますが、コンポーネントのプロパティ アクセサーの呼び出しをインターセプトし、 によって、デザイナーは、ユーザーによって設定された値を追跡して、必要に応じてその値を渡すように設計されているコンポーネントにします。  
  
 この例で、<xref:System.Windows.Forms.Control.Visible%2A>と<xref:System.Windows.Forms.Control.Enabled%2A>でプロパティをシャドウは、`MarqueeBorderDesigner`からユーザーを防ぐことが、`MarqueeBorder`コントロールを非表示またはデザイン時に無効です。  
  
 デザイナーは、追加し、プロパティを削除することができますもできます。 この例で、<xref:System.Windows.Forms.Control.Padding%2A>ためにそのプロパティが、デザイン時に削除された、`MarqueeBorder`コントロールで指定された光源のサイズに基づいての余白をプログラムで設定する、`LightSize`プロパティです。  
  
 基本クラス`MarqueeBorderDesigner`は<xref:System.ComponentModel.Design.ComponentDesigner>属性、プロパティ、およびデザイン時にコントロールによって公開されているイベントに変更できるメソッドを持ちます。  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 これらのメソッドを使用して、コンポーネントのパブリック インターフェイスを変更する場合は、これらの規則を行う必要があります。  
  
-   項目の追加または削除、`PreFilter`メソッドにのみ  
  
-   既存の項目を変更、`PostFilter`メソッドにのみ  
  
-   基本実装を最初に呼び出す常に、`PreFilter`メソッド  
  
-   基本実装を最後呼び出す常に、`PostFilter`メソッド  
  
 これらの規則に従うことにより、デザイン時環境のすべてのデザイナーのように設計されているすべてのコンポーネントの一貫した表示できます。  
  
 <xref:System.ComponentModel.Design.ComponentDesigner>クラスが特定のインスタンス変数を作成する必要がなくなるが影付きのプロパティの値を管理するためのディクショナリを提供します。  
  
#### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>シャドウとフィルターのプロパティにカスタム デザイナーを作成するには  
  
1.  右クリックし、**デザイン**フォルダーと、新しいクラスを追加します。 ソース ファイルの"MarqueeBorderDesigner"ベースの名前を付けます  
  
2.  開く、`MarqueeBorderDesigner`内のソース ファイル、**コード エディター**です。 ファイルの上部には、次の名前空間をインポートします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  宣言を変更する`MarqueeBorderDesigner`から継承する<xref:System.Windows.Forms.Design.ParentControlDesigner>です。  
  
     `MarqueeBorder`コントロールで子コントロールを含めることができます`MarqueeBorderDesigner`から継承<xref:System.Windows.Forms.Design.ParentControlDesigner>親と子の対話を処理します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  基本実装をオーバーライド<xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>です。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  <xref:System.Windows.Forms.Control.Enabled%2A> プロパティと <xref:System.Windows.Forms.Control.Visible%2A> プロパティを実装します。 これらの実装では、コントロールのプロパティをシャドウします。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## <a name="handling-component-changes"></a>コンポーネントの変更の処理  
 `MarqueeControlRootDesigner`クラスは、カスタムのデザイン時のエクスペリエンスを提供、`MarqueeControl`インスタンス。 デザイン時の機能の大部分がから継承されます、<xref:System.Windows.Forms.Design.DocumentDesigner>クラス以外の特定の 2 つのカスタマイズを実装するコードは、: コンポーネントの変更を処理して、デザイナー動詞を追加します。  
  
 ユーザー設計としてその`MarqueeControl`、インスタンスのルート デザイナーに変更の追跡は、`MarqueeControl`とその子コントロール。 デザイン時環境は、便利なサービスを提供<xref:System.ComponentModel.Design.IComponentChangeService>コンポーネントの状態に変更を追跡します。  
  
 環境を照会することによってこのサービスへの参照を取得する、<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>メソッドです。 デザイナーがのハンドラーをアタッチできますクエリが成功した場合、<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged>イベントし、デザイン時に一貫性のある状態を維持するために必要なタスクを実行します。  
  
 場合、`MarqueeControlRootDesigner`呼び出しは、クラス、<xref:System.Windows.Forms.Control.Refresh%2A>メソッドごとに`IMarqueeWidget`オブジェクトに含まれる、`MarqueeControl`です。 これにより、`IMarqueeWidget`プロパティがその親のような場合に適切に再描画するオブジェクト<xref:System.Windows.Forms.Control.Size%2A>変更されます。  
  
#### <a name="to-handle-component-changes"></a>コンポーネントの変更を処理するには  
  
1.  開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**をオーバーライドし、<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>メソッドです。 基本実装を呼び出す<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>クエリを実行し、<xref:System.ComponentModel.Design.IComponentChangeService>です。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  実装、<xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>イベント ハンドラー。 テストの送信側のコンポーネントの種類である場合と、 `IMarqueeWidget`、呼び出すその<xref:System.Windows.Forms.Control.Refresh%2A>メソッド。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## <a name="adding-designer-verbs-to-your-custom-designer"></a>カスタム デザイナー動詞を追加します。  
 デザイナー動詞は、イベント ハンドラーにリンクされているメニュー コマンドです。 デザイナー動詞は、デザイン時コンポーネントのショートカット メニューに追加されます。 詳細については、「<xref:System.ComponentModel.Design.DesignerVerb>」を参照してください。  
  
 2 つのデザイナー動詞は、デザイナーに追加:**テストの実行**と**テストの停止**です。 これらの動詞には、実行時の動作を表示することが、`MarqueeControl`デザイン時にします。 これらの動詞に追加されます、`MarqueeControlRootDesigner`です。  
  
 ときに**テストの実行**が呼び出されると、動詞のイベント ハンドラーを呼び出す、`StartMarquee`メソッドを`MarqueeControl`です。 ときに**テストの停止**が呼び出されると、動詞のイベント ハンドラーを呼び出す、`StopMarquee`メソッドを`MarqueeControl`です。 実装、`StartMarquee`と`StopMarquee`メソッドを実装するコンテナー内のコントロールでこれらのメソッドを呼び出す`IMarqueeWidget`すべて含まれている、`IMarqueeWidget`コントロールも、テストに参加します。  
  
#### <a name="to-add-designer-verbs-to-your-custom-designers"></a>デザイナー動詞をカスタム デザイナーに追加するには  
  
1.  `MarqueeControlRootDesigner`クラス、という名前のイベント ハンドラー追加`OnVerbRunTest`と`OnVerbStopTest`です。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  これらのイベント ハンドラーを対応するデザイナー動詞に接続します。 `MarqueeControlRootDesigner` 継承、<xref:System.ComponentModel.Design.DesignerVerbCollection>その基本クラスからです。 2 つ作成する新しい<xref:System.ComponentModel.Design.DesignerVerb>内のこのコレクションに追加して、オブジェクト、<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>メソッドです。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## <a name="creating-a-custom-uitypeeditor"></a>カスタム  
 ユーザーのカスタム設計時の操作を作成するときに、[プロパティ] ウィンドウとカスタム操作を作成することが望ましいは多くの場合です。 これを行うに作成することで、<xref:System.Drawing.Design.UITypeEditor>です。 詳細については、次を参照してください。[する方法: UI 型エディターを作成する](http://msdn.microsoft.com/library/292c6e33-8d85-4012-9b51-05835a6f6dfd)です。  
  
 `MarqueeBorder`コントロールのプロパティ ウィンドウでいくつかのプロパティを公開します。 これらのプロパティの 2 つの`MarqueeSpinDirection`と`MarqueeLightShape`列挙体によって表されます。 UI 型エディターの使用方法を説明する、`MarqueeLightShape`プロパティが関連付けられている必要がある<xref:System.Drawing.Design.UITypeEditor>クラスです。  
  
#### <a name="to-create-a-custom-ui-type-editor"></a>カスタムの UI 型エディターを作成するには  
  
1.  開く、`MarqueeBorder`内のソース ファイル、**コード エディター**です。  
  
2.  定義で、`MarqueeBorder`クラスと呼ばれるクラスを宣言`LightShapeEditor`から派生した<xref:System.Drawing.Design.UITypeEditor>です。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  宣言、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>インスタンス変数と呼ばれる`editorService`です。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> メソッドをオーバーライドします。 この実装を返します<xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>、デザイン環境を表示する方法を指示する、`LightShapeEditor`です。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> メソッドをオーバーライドします。 この実装は、デザイン環境、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>オブジェクト。 成功すると、作成、`LightShapeSelectionControl`です。 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>を開始するメソッドが呼び出され、`LightShapeEditor`です。 この呼び出しからの戻り値は、デザイン環境に返されます。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>カスタムのビュー コントロールの作成  
  
1.  `MarqueeLightShape`プロパティには、ライトの図形の 2 種類がサポートしています:`Square`と`Circle`です。 [プロパティ] ウィンドウで、これらの値をグラフィカルに表示するためだけに使用するカスタム コントロールを作成します。 このカスタム コントロールで使用される、<xref:System.Drawing.Design.UITypeEditor>プロパティ ウィンドウと対話します。  
  
#### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>カスタム UI 型エディターのビュー コントロールを作成するには  
  
1.  新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlLibrary`プロジェクト。 新しいソース ファイル"LightShapeSelectionControl"の基本の名前を付けます  
  
2.  2 つをドラッグして<xref:System.Windows.Forms.Panel>から制御、**ツールボックス**上に、`LightShapeSelectionControl`です。 名前を付けます`squarePanel`と`circlePanel`です。 サイド バイ サイドそれらを配置します。 設定、<xref:System.Windows.Forms.Control.Size%2A>両方のプロパティ<xref:System.Windows.Forms.Panel>コントロールを (60、60)。 設定、<xref:System.Windows.Forms.Control.Location%2A>のプロパティ、`squarePanel`に制御を (8, 10)。 設定、<xref:System.Windows.Forms.Control.Location%2A>のプロパティ、`circlePanel`に制御を (80, 10)。 最後に、設定、<xref:System.Windows.Forms.Control.Size%2A>のプロパティ、`LightShapeSelectionControl`に (150、80)。  
  
3.  開く、`LightShapeSelectionControl`内のソース ファイル、**コード エディター**です。 ファイルの上部には、インポート、<xref:System.Windows.Forms.Design?displayProperty=nameWithType>名前空間。  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  実装<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、`squarePanel`と`circlePanel`コントロール。 これらのメソッドを呼び出す<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>カスタムを終了する<xref:System.Drawing.Design.UITypeEditor>セッションを編集します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  宣言、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>インスタンス変数と呼ばれる`editorService`です。  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  宣言、`MarqueeLightShape`インスタンス変数と呼ばれる`lightShapeValue`です。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  `LightShapeSelectionControl`コンス トラクター、アタッチ、<xref:System.Windows.Forms.Control.Click>へのイベント ハンドラー、`squarePanel`と`circlePanel`コントロールの<xref:System.Windows.Forms.Control.Click>イベント。 また、割り当てをコンス トラクター オーバー ロードを定義、`MarqueeLightShape`デザイン環境から値、`lightShapeValue`フィールドです。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  <xref:System.ComponentModel.Component.Dispose%2A>メソッド、デタッチ、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。 ファイルを開き、LightShapeSelectionControl.Designer.cs または LightShapeSelectionControl.Designer.vb の既定の定義を削除、<xref:System.ComponentModel.Component.Dispose%2A>メソッドです。  
  
5.  `LightShape` プロパティを実装します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドします。 この実装は、塗りつぶされた四角形と円を描画します。 また、どちらか 1 つの図形の周囲に罫線を描画することによって、選択した値を強調表示します。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## <a name="testing-your-custom-control-in-the-designer"></a>デザイナーでカスタム コントロールのテスト  
 この時点では、ビルドすることができます、`MarqueeControlLibrary`プロジェクト。 継承されるコントロールを作成することで実装をテスト、`MarqueeControl`クラスおよびフォーム上で使用します。  
  
#### <a name="to-create-a-custom-marqueecontrol-implementation"></a>カスタム MarqueeControl 実装を作成するには  
  
1.  Windows フォーム デザイナーで `DemoMarqueeControl` を開きます。 このインスタンスを作成、`DemoMarqueeControl`を入力し、それのインスタンスの表示、`MarqueeControlRootDesigner`型です。  
  
2.  **ツールボックス**を開き、**にコンポーネント**タブです。表示されます、`MarqueeBorder`と`MarqueeText`コントロールの選択に使用できます。  
  
3.  インスタンスをドラッグして、`MarqueeBorder`コントロールを`DemoMarqueeControl`デザイン サーフェイスです。 このドッキング`MarqueeBorder`コントロールを親コントロールです。  
  
4.  インスタンスをドラッグして、`MarqueeText`コントロールを`DemoMarqueeControl`デザイン サーフェイスです。  
  
5.  ソリューションをビルドします。  
  
6.  右クリックし、`DemoMarqueeControl`ショートカット メニューを選択し、**テストの実行**アニメーションを開始するにはオプションです。 をクリックして**テストの停止**アニメーションを停止します。  
  
7.  開いている**Form1**デザイン ビューでします。  
  
8.  2 つの配置<xref:System.Windows.Forms.Button>フォーム上のコントロールです。 名前を付けます`startButton`と`stopButton`、し、変更、<xref:System.Windows.Forms.Control.Text%2A>プロパティ値を**開始**と**停止**、それぞれします。  
  
9. 実装<xref:System.Windows.Forms.Control.Click>両方のイベント ハンドラー<xref:System.Windows.Forms.Button>コントロール。  
  
10. **ツールボックス**を開き、**ためコンポーネント**タブです。表示されます、`DemoMarqueeControl`選択に使用できます。  
  
11. インスタンスをドラッグ`DemoMarqueeControl`上に、 **Form1**デザイン サーフェイスです。  
  
12. <xref:System.Windows.Forms.Control.Click>イベント ハンドラーを呼び出す、`Start`と`Stop`のメソッド、`DemoMarqueeControl`です。  
  
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
  
1.  設定、`MarqueeControlTest`プロジェクトをスタートアップ プロジェクトとして使用し、実行します。 表示するフォームが表示されます、`DemoMarqueeControl`です。 クリックして、**開始**アニメーションを開始するボタンをクリックします。 テキストが点滅し、光が境界線を移動するはずです。  
  
## <a name="next-steps"></a>次の手順  
 `MarqueeControlLibrary`カスタム コントロールと関連付けられたデザイナーの単純な実装を示します。 いくつかの方法で行うと、このサンプルがより高度です。  
  
-   プロパティ値を変更、`DemoMarqueeControl`デザイナーでします。 さらに追加`MarqueBorder`を制御し、入れ子になった効果を作成するには、その親インスタンス内にドッキングします。 さまざまな設定と実験、`UpdatePeriod`と光に関連するプロパティです。  
  
-   独自の実装を作成`IMarqueeWidget`です。 複数のイメージで、点滅"またはアニメーション化されたサインインを作成することなど。  
  
-   さらに、デザイン時のエクスペリエンスをカスタマイズします。 多くのプロパティをシャドウを試して<xref:System.Windows.Forms.Control.Enabled%2A>と<xref:System.Windows.Forms.Control.Visible%2A>、し、新しいプロパティを追加することができます。 子コントロールのドッキングなどの一般的なタスクを簡略化する新しいデザイナー動詞を追加します。  
  
-   ライセンス、`MarqueeControl`です。 詳細については、次を参照してください。[する方法: ライセンス コンポーネントやコントロール](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)です。  
  
-   コントロールをシリアル化する方法と、それらのコードを生成する方法を制御します。 詳細については、次を参照してください。[動的ソース コードの生成とコンパイル](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Design.ParentControlDesigner>  
 <xref:System.Windows.Forms.Design.DocumentDesigner>  
 <xref:System.ComponentModel.Design.IRootDesigner>  
 <xref:System.ComponentModel.Design.DesignerVerb>  
 <xref:System.Drawing.Design.UITypeEditor>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [方法: デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)  
 [デザイン時サポートの拡張](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [カスタム デザイナー](http://msdn.microsoft.com/library/ca11988e-d38e-44d8-a05d-71362ae7844d)  
 [.NET 図形ライブラリ: サンプル デザイナー](http://windowsforms.net/articles/shapedesigner.aspx)
