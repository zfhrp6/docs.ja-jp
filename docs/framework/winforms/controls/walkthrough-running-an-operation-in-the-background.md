---
title: "チュートリアル : 操作をバックグラウンドで実行する | Microsoft Docs"
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
  - "バックグラウンド スレッド"
  - "BackgroundWorker クラス, 例"
  - "フォーム, バックグラウンド操作"
  - "フォーム, マルチスレッド"
  - "スレッド処理 [Windows フォーム], バックグラウンド操作"
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# チュートリアル : 操作をバックグラウンドで実行する
完了するまでに時間がかかる操作があり、ユーザー インターフェイスが遅くならないようにする場合は、<xref:System.ComponentModel.BackgroundWorker> クラスを使用して別のスレッドで操作を実行できます。  
  
 ここで使用するコード例の完全なリストについては、「[方法 : バックグラウンドで操作を実行する](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 操作をバックグラウンドで実行するには  
  
1.  Windows フォーム デザイナーでフォームをアクティブにした状態で、**ツールボックス**から 2 つの <xref:System.Windows.Forms.Button> コントロールをフォームにドラッグし、ボタンの `Name` プロパティおよび <xref:System.Windows.Forms.Control.Text%2A> プロパティを以下の表のとおりに設定します。  
  
    |ボタン|名前|テキスト|  
    |---------|--------|----------|  
    |`button1`|`startBtn`|\[開始\]|  
    |`button2`|`cancelBtn`|\[キャンセル\]|  
  
2.  **ツールボックス**を開き、**\[コンポーネント\]** タブをクリックします。次に、<xref:System.ComponentModel.BackgroundWorker> コンポーネントをフォームにドラッグします。  
  
     `backgroundWorker1` コンポーネントが、**コンポーネント トレイ**に表示されます。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> プロパティを `true` に設定します。  
  
4.  **\[プロパティ\]** ウィンドウの **\[イベント\]** ボタンをクリックし、<xref:System.ComponentModel.BackgroundWorker.DoWork> イベントおよび <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベントをダブルクリックしてイベント ハンドラーを作成します。  
  
5.  完了するまでに時間のかかるコードを <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーに挿入します。  
  
6.  操作に必要なパラメーターを <xref:System.ComponentModel.DoWorkEventArgs> パラメーターの <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> プロパティから抽出します。  
  
7.  計算の結果を <xref:System.ComponentModel.DoWorkEventArgs> の <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> プロパティに代入します。  
  
     この値は、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーで使用できます。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  操作の結果を取得するコードを <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーに挿入します。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. `TimeConsumingOperation` メソッドを実装します。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. Windows フォーム デザイナーで `startButton` をダブルクリックして <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成します。  
  
11. `startButton` の <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> メソッドを呼び出します。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. Windows フォーム デザイナーで `cancelButton` をダブルクリックして <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成します。  
  
13. `cancelButton` の <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> メソッドを呼び出します。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. ファイルの先頭に System.ComponentModel and System.Threading 名前空間をインポートします。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. F6 を押してソリューションをビルドした後で、Ctrl キーを押しながら F5 キーを押してアプリケーションをデバッガーの外部で実行します。  
  
> [!NOTE]
>  F5 キーを押してアプリケーションをデバッガーの内部で実行した場合、`TimeConsumingOperation` メソッド内で発生する例外がデバッガーにキャッチされ、表示されます。  アプリケーションをデバッガーの外部で実行すると、<xref:System.ComponentModel.BackgroundWorker> が例外を処理し、<xref:System.ComponentModel.RunWorkerCompletedEventArgs> の <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> プロパティにキャッシュします。  
  
1.  非同期操作を実行するには **\[開始\]** をクリックし、非同期操作の実行を停止するには **\[キャンセル\]** をクリックします。  
  
     各操作の結果は、<xref:System.Windows.Forms.MessageBox> に表示されます。  
  
## 次の手順  
  
-   非同期操作の進行状況を通知するフォームを実装します。  詳細については、「[方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)」を参照してください。  
  
-   コンポーネント向けの非同期パターンをサポートするクラスを実装します。  詳細については、「[Implementing the Event\-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)」を参照してください。  
  
## 参照  
 <xref:System.ComponentModel.BackgroundWorker>   
 <xref:System.ComponentModel.DoWorkEventArgs>   
 [方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [方法 : バックグラウンドで操作を実行する](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)