---
title: "チュートリアル : バックグラウンド操作を使用するフォームの実装"
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
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c12892c4761f0158153c87464066dd727c83bfc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>チュートリアル : バックグラウンド操作を使用するフォームの実装
完了するには長い時間がかかる操作があると応答を停止する、ユーザー インターフェイス (UI) を設定したくない、または「ハング」しを使用できる場合、<xref:System.ComponentModel.BackgroundWorker>別のスレッドで操作を実行するクラス。  
  
 このチュートリアルを使用する方法について説明、 <xref:System.ComponentModel.BackgroundWorker> ""バック グラウンドで時間がかかる計算を実行するクラス、ユーザー インターフェイスに応答したままです。  このチュートリアルを完了すると、フィボナッチ数を非同期に計算するアプリケーションが作成されます。 大きなフィボナッチ数の計算にはかなりの時間がかかることがありますが、この遅延によってメイン UI スレッドが中断されることはなく、計算中もフォームは応答性を維持します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows ベースのアプリケーションの作成  
  
-   作成する、<xref:System.ComponentModel.BackgroundWorker>フォーム  
  
-   非同期イベント ハンドラーの追加  
  
-   進行状況の報告とキャンセルのサポートの追加  
  
 この例で使用するコード全体については、「[方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 まず、プロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>バックグラウンド操作を使用するフォームを作成するには  
  
1.  `BackgroundWorkerExample` という Windows ベースのアプリケーション プロジェクトを作成します。 詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **ソリューション エクスプローラー**で、**[Form1]** を右クリックし、ショートカット メニューの **[名前の変更]** をクリックします。 ファイル名を `FibonacciCalculator` に変更します。 コード要素 "`Form1`" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。  
  
3.  ドラッグ、<xref:System.Windows.Forms.NumericUpDown>から制御、**ツールボックス**フォーム上にします。 設定、<xref:System.Windows.Forms.NumericUpDown.Minimum%2A>プロパティを`1`と<xref:System.Windows.Forms.NumericUpDown.Maximum%2A>プロパティを`91`です。  
  
4.  2 つ追加<xref:System.Windows.Forms.Button>フォームのコントロールです。  
  
5.  最初の名前を変更<xref:System.Windows.Forms.Button>コントロール`startAsyncButton`設定と、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`Start Async`です。 2 番目の名前を変更<xref:System.Windows.Forms.Button>コントロール`cancelAsyncButton`、設定と、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`Cancel Async`です。 設定の<xref:System.Windows.Forms.Control.Enabled%2A>プロパティを`false`です。  
  
6.  両方のイベント ハンドラーを作成、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント。 詳細については、「[方法 : デザイナーを使用してイベント ハンドラーを作成する](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)」を参照してください。  
  
7.  ドラッグ、<xref:System.Windows.Forms.Label>から制御、**ツールボックス**をフォームに名前を変更および`resultLabel`です。  
  
8.  ドラッグ、<xref:System.Windows.Forms.ProgressBar>から制御、**ツールボックス**フォーム上にします。  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>フォームでの BackgroundWorker の作成  
 作成することができます、 <xref:System.ComponentModel.BackgroundWorker> 、非同期操作を使用するため、 **Windows** **フォーム デザイナー**です。  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>デザイナーを使用して BackgroundWorker を作成するには  
  
-   **コンポーネント**のタブ、**ツールボックス**、ドラッグ、<xref:System.ComponentModel.BackgroundWorker>フォーム上にします。  
  
## <a name="adding-asynchronous-event-handlers"></a>非同期イベント ハンドラーの追加  
 イベント ハンドラーを追加する準備が整いました、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの非同期イベントです。 バックグラウンドで実行される時間のかかる操作 (フィボナッチ数の計算) は、これらのイベント ハンドラーのいずれかによって呼び出されます。  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>非同期イベント ハンドラーを実装するには  
  
1.  **プロパティ** ウィンドウで、<xref:System.ComponentModel.BackgroundWorker>が選択されているコンポーネントをクリックして、**イベント**ボタンをクリックします。 ダブルクリックして、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベントをイベント ハンドラーを作成します。 イベント ハンドラーの使用方法の詳細については、「[方法 : デザイナーを使用してイベント ハンドラーを作成する](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)」を参照してください。  
  
2.  フォームで `ComputeFibonacci` という新しいメソッドを作成します。 このメソッドがバックグラウンドで実行され、実際の処理を行います。 このコードは、フィボナッチ アルゴリズムの再帰的実装を示しています。これは、非常に非効率であり、数が大きくなるにつれて、完了までの所要時間が急激に増大します。 ここでは、アプリケーションで長時間の遅延が発生する可能性のある操作を示すために、このコードを使用しています。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  <xref:System.ComponentModel.BackgroundWorker.DoWork> 、イベント ハンドラー呼び出しを追加して、`ComputeFibonacci`メソッドです。 最初のパラメーターを受け取る`ComputeFibonacci`から、<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>です。 <xref:System.ComponentModel.BackgroundWorker>と<xref:System.ComponentModel.DoWorkEventArgs>パラメーターは、進行状況レポートとキャンセルを後で使用するをサポートします。 戻り値を割り当てる`ComputeFibonacci`を<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>です。 この結果は使用可能になります、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラーを参照していません、`backgroundWorker1`これの特定のインスタンスにこのイベント ハンドラーを結合すると、変数を直接インスタンス<xref:System.ComponentModel.BackgroundWorker>です。 代わりへの参照、<xref:System.ComponentModel.BackgroundWorker>これが発生するイベントがから復元される、`sender`パラメーター。 これは、フォームが少なくとも 1 つをホストするときに重要な<xref:System.ComponentModel.BackgroundWorker>します。 内のユーザー インターフェイス オブジェクトを操作していない重要なも、<xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラー。 代わりに、ユーザー インターフェイスを介しての通信、<xref:System.ComponentModel.BackgroundWorker>イベント。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  `startAsyncButton`コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラー、非同期操作を開始するコードを追加します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 、イベント ハンドラーに計算の結果を割り当てる、`resultLabel`コントロール。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>進行状況の報告とキャンセルのサポートの追加  
 時間のかかる非同期操作では、多くの場合、進行状況をユーザーに報告し、ユーザーが操作をキャンセルできるようにすることが望まれます。 <xref:System.ComponentModel.BackgroundWorker>クラスとして、バック グラウンド操作が実行の進行状況を投稿することができますイベントを提供します。 呼び出しを検出するために、ワーカーのコードを許可するフラグも用意されています。<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>され自体を中断します。  
  
#### <a name="to-implement-progress-reporting"></a>進行状況の報告を実装するには  
  
1.  **[プロパティ]** ウィンドウで `backgroundWorker1` を選択します。 <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> と <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> プロパティを `true` に設定します。  
  
2.  `FibonacciCalculator` フォームで 2 つの変数を宣言します。 これらの変数を使用して進行状況を追跡します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントのイベント ハンドラーを追加します。 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラー、update、<xref:System.Windows.Forms.ProgressBar>で、<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>のプロパティ、<xref:System.ComponentModel.ProgressChangedEventArgs>パラメーター。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>キャンセルのサポートを実装するには  
  
1.  `cancelAsyncButton`コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラー、非同期操作をキャンセルするコードを追加します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  `ComputeFibonacci` メソッドの次のコード フラグメントは、進行状況の報告とキャンセルのサポートを示しています。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点で、フィボナッチ電卓アプリケーションをコンパイルして実行できます。  
  
#### <a name="to-test-your-project"></a>プロジェクトをテストするには  
  
-   F5 キーを押してアプリケーションをコンパイルし、実行します。  
  
     計算の実行中は、バック グラウンドで表示されます、<xref:System.Windows.Forms.ProgressBar>完了するまで計算の進行状況を表示します。 また、保留中の操作をキャンセルすることもできます。  
  
     数値が小さい場合、計算に時間はかかりませんが、数値が大きくなると、大幅な遅延が発生します。 30 以上の値を入力した場合、コンピューターの速度によっては数秒の遅延が発生します。 値が 40 を超えると、計算が終了するまでに数分から数時間かかることがあります。 電卓が大きなフィボナッチ数を計算している間も、フォームの移動、最小化、最大化を自由に行うことができ、フォームを閉じることもできます。 これは、メイン UI スレッドが計算の終了を待機していないためです。  
  
## <a name="next-steps"></a>次の手順  
 使用するフォームを実装している、<xref:System.ComponentModel.BackgroundWorker>バック グラウンドで計算を実行するためのコンポーネントの非同期操作の他の使用法を調べることができます。  
  
-   複数回使用<xref:System.ComponentModel.BackgroundWorker>並行処理のいくつかのオブジェクト。  
  
-   マルチスレッド アプリケーションをデバッグする方法については、「[方法 : [スレッド] ウィンドウを使用する](/visualstudio/debugger/how-to-use-the-threads-window)」を参照してください。  
  
-   非同期プログラミング モデルをサポートする独自のコンポーネントを実装する。 詳細については、「[イベント ベースの非同期パターンの概要](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)」を参照してください。  
  
    > [!CAUTION]
    >  どのような種類のマルチスレッドを使用している場合でも、非常に深刻で複雑なバグを引き起こしてしまう可能性があります。 マルチスレッドを使用するソリューションを実装する前に、「[マネージ スレッド処理の実施](../../../../docs/standard/threading/managed-threading-best-practices.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.ComponentModel.BackgroundWorker>  
 [マネージ スレッド処理の実施](../../../../docs/standard/threading/managed-threading-best-practices.md)  
 [コンポーネントのマルチスレッド](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [NOT IN BUILD: Visual Basic でのマルチ スレッド](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [方法: バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [チュートリアル: 操作をバックグラウンドで実行する](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 [BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
