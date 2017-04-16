---
title: "チュートリアル : バックグラウンド操作を使用するフォームの実装 | Microsoft Docs"
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
  - "バックグラウンド操作"
  - "バックグラウンド タスク"
  - "BackgroundWorker コンポーネント"
  - "フォーム, バックグラウンド操作"
  - "フォーム, マルチスレッド"
  - "スレッド処理 [Windows フォーム], バックグラウンド操作"
  - "スレッド処理 [Windows フォーム], フォーム"
  - "スレッド処理 [Windows フォーム], チュートリアル"
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# チュートリアル : バックグラウンド操作を使用するフォームの実装
完了するまで時間がかかる操作があり、操作中にユーザー インターフェイス \(UI\) が応答を停止 \(つまり "ハングアップ"\) しないようにするには、<xref:System.ComponentModel.BackgroundWorker> クラスを使用して操作を別のスレッドで実行できます。  
  
 このチュートリアルでは、<xref:System.ComponentModel.BackgroundWorker> クラスを使用して、時間のかかる計算を "バックグラウンドで" 実行しながら、ユーザー インターフェイスの応答性を維持する方法について説明します。  ここでは、フィボナッチの数列を非同期的に計算するアプリケーションを作成します。  大きなフィボナッチ数の計算には、著しく時間がかかることがありますが、メイン UI スレッドは、この遅延によって中断されず、計算の間、フォームは応答性を維持します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows ベース アプリケーションの作成  
  
-   フォームでの <xref:System.ComponentModel.BackgroundWorker> の作成  
  
-   非同期イベント ハンドラーの追加  
  
-   進行状況の報告機能とキャンセルのサポートの追加  
  
 この例で使用するコードの完全な一覧については、「[方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### バックグラウンド操作を使用するフォームを作成するには  
  
1.  `BackgroundWorkerExample` という名前の Windows ベース アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **ソリューション エクスプローラー**で、**\[Form1\]** を右クリックし、ショートカット メニューの **\[名前の変更\]** をクリックします。  ファイル名を `FibonacciCalculator` に変更します。  コード要素 "`Form1`" へのすべての参照の名前を変更するかどうかを確認するダイアログ ボックスが表示されたら、**\[はい\]** をクリックします。  
  
3.  **\[ツールボックス\]** の <xref:System.Windows.Forms.NumericUpDown> コントロールをフォームにドラッグします。  <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> プロパティを `1`、<xref:System.Windows.Forms.NumericUpDown.Maximum%2A> プロパティを `91` に設定します。  
  
4.  2 つの <xref:System.Windows.Forms.Button> コントロールをフォームに追加します。  
  
5.  一方の <xref:System.Windows.Forms.Button> コントロールの名前を `startAsyncButton` に変更し、<xref:System.Windows.Forms.Control.Text%2A> プロパティを `Start Async` に設定します。  もう一方の <xref:System.Windows.Forms.Button> コントロールの名前を `cancelAsyncButton` に変更し、<xref:System.Windows.Forms.Control.Text%2A> プロパティを `Cancel Async` に設定します。  <xref:System.Windows.Forms.Control.Enabled%2A> プロパティを `false` に設定します。  
  
6.  両方の <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベントに対するイベント ハンドラーを作成します。  詳細については、「[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/ja-jp/8461e9b8-14e8-406f-936e-3726732b23d2)」を参照してください。  
  
7.  **\[ツールボックス\]** の <xref:System.Windows.Forms.Label> コントロールをフォームにドラッグし、名前を `resultLabel` に変更します。  
  
8.  **\[ツールボックス\]** の <xref:System.Windows.Forms.ProgressBar> コントロールをフォームにドラッグします。  
  
## フォームでの BackgroundWorker の作成  
 非同期操作用の <xref:System.ComponentModel.BackgroundWorker> は、**Windows** **フォーム デザイナー** を使用して作成できます。  
  
#### デザイナーを使用して BackgroundWorker を作成するには  
  
-   **\[ツールボックス\]** の **\[コンポーネント\]** タブから、<xref:System.ComponentModel.BackgroundWorker> をフォームにドラッグします。  
  
## 非同期イベント ハンドラーの追加  
 以上で、<xref:System.ComponentModel.BackgroundWorker> コンポーネントの非同期イベント用のイベント ハンドラーを追加する準備ができました。  バックグラウンドで実行する、時間のかかるフィボナッチ数列の計算操作は、これらのうちいずれかのイベント ハンドラーによって呼び出されます。  
  
#### 非同期イベント ハンドラーを実装するには  
  
1.  **\[プロパティ\]** ウィンドウで <xref:System.ComponentModel.BackgroundWorker> コンポーネントが選択されている状態で、**\[イベント\]** ボタンをクリックします。  <xref:System.ComponentModel.BackgroundWorker.DoWork> イベントと <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベントをダブルクリックして、イベント ハンドラーを作成します。  イベント ハンドラーの使用方法の詳細については、「[How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/ja-jp/8461e9b8-14e8-406f-936e-3726732b23d2)」を参照してください。  
  
2.  フォームで `ComputeFibonacci` という名前の新しいメソッドを作成します。  このメソッドが実際の操作を実行し、バックグラウンドで動作します。  このコードは、フィボナッチ アルゴリズムの反復実装を示しています。これは、著しく非効率な操作で、数が大きくなるにつれて、完了するまでにかかる時間が急激に長くなります。  アプリケーションで大きな遅延が発生する操作の例として、このコードを使用します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーで、`ComputeFibonacci` メソッドの呼び出しを追加します。  `ComputeFibonacci` の最初のパラメーターを、<xref:System.ComponentModel.DoWorkEventArgs> の <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> プロパティから受け取ります。  <xref:System.ComponentModel.BackgroundWorker> パラメーターと <xref:System.ComponentModel.DoWorkEventArgs> パラメーターは、進行状況の報告機能とキャンセルのサポートのために後で使用します。  `ComputeFibonacci` の戻り値を <xref:System.ComponentModel.DoWorkEventArgs> の <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> プロパティに代入します。  この結果は、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーで利用できるようになります。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーは、`backgroundWorker1` インスタンス変数を直接参照しません。直接参照すると、このイベント ハンドラーが <xref:System.ComponentModel.BackgroundWorker> の特定のインスタンスに結合されるためです。  代わりに、該当するイベントを生成した <xref:System.ComponentModel.BackgroundWorker> への参照は、`sender` パラメーターから復元します。  このことは、フォームが複数の <xref:System.ComponentModel.BackgroundWorker> をホストする場合に重要です。  また、<xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーでユーザー インターフェイス オブジェクトを操作しないようにしてください。  代わりに、<xref:System.ComponentModel.BackgroundWorker> のイベントを通じてユーザー インターフェイスと通信します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  `startAsyncButton` コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで、非同期操作を開始するコードを追加します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーで、`resultLabel` コントロールに計算結果を代入します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## 進行状況の報告機能とキャンセルのサポートの追加  
 時間のかかる非同期操作では、進行状況をユーザーに報告し、ユーザーが操作をキャンセルできるようにすることが望まれます。  <xref:System.ComponentModel.BackgroundWorker> クラスには、バックグラウンド操作の進行状況を報告できるイベントが用意されています。  また、ワーカー コードで <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> の呼び出しを検出し、ワーカー コード自体を中断できるようにするフラグも使用できます。  
  
#### 進行状況の報告機能を実装するには  
  
1.  **\[プロパティ\]** ウィンドウで `backgroundWorker1` を選択します。  <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> プロパティと <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> プロパティを `true` に設定します。  
  
2.  `FibonacciCalculator` フォームで 2 つの変数を宣言します。  これらの変数を使用して、進行状況を追跡します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントのイベント ハンドラーを追加します。  <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベント ハンドラーで、<xref:System.ComponentModel.ProgressChangedEventArgs> パラメーターの <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> プロパティを使用して、<xref:System.Windows.Forms.ProgressBar> を更新します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### キャンセルのサポートを実装するには  
  
1.  `cancelAsyncButton` コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで、非同期操作をキャンセルするコードを追加します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  進行状況を報告し、キャンセルをサポートする `ComputeFibonacci` メソッドのコード片を次に示します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## チェックポイント  
 この時点で、フィボナッチ電卓アプリケーションをコンパイルして実行できます。  
  
#### プロジェクトをテストするには  
  
-   F5 キーを押してアプリケーションをコンパイルおよび実行します。  
  
     計算がバックグラウンドで実行されている間、計算が完了するまでの進行状況が <xref:System.Windows.Forms.ProgressBar> に表示されます。  また、保留中の操作をキャンセルすることもできます。  
  
     小さい数の場合は計算に時間がかかりませんが、大きい数の場合は著しい遅延が生じます。  30 以上の値を入力した場合、コンピューターの処理速度によっては、数秒間の遅延が生じます。  値が 40 以上の場合は、計算が終了するまでに数分から数時間かかることがあります。  電卓が大きなフィボナッチ数を計算している間でも、フォームを自由に移動したり、拡大縮小したり、閉じたりすることもできるます。  これは、メイン UI スレッドが、計算の終了を待機していないからです。  
  
## 次の手順  
 これで、バックグラウンドで計算を実行する <xref:System.ComponentModel.BackgroundWorker> コンポーネントを使用するフォームを実装できました。この後は、次のような非同期操作の他の可能性を検討してください。  
  
-   複数の <xref:System.ComponentModel.BackgroundWorker> オブジェクトを使用して、複数の同時操作を実行する。  
  
-   マルチスレッド アプリケーションをデバッグするには、「[方法 : \[スレッド\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)」を参照してください。  
  
-   非同期プログラミング モデルをサポートする独自のコンポーネントを実装する。  詳細については、「[Event\-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)」を参照してください。  
  
    > [!CAUTION]
    >  どのような種類のマルチスレッドを使用している場合でも、非常に深刻で複雑なバグを引き起こしてしまう可能性があります。  マルチスレッドを使用するソリューションを実装する前に、「[Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)」を参照してください。  
  
## 参照  
 <xref:System.ComponentModel.BackgroundWorker>   
 [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md)   
 [コンポーネントのマルチスレッド](../Topic/Multithreading%20in%20Components.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/ja-jp/c731a50c-09c1-4468-9646-54c86b75d269)   
 [方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [チュートリアル : 操作をバックグラウンドで実行する](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)   
 [BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)