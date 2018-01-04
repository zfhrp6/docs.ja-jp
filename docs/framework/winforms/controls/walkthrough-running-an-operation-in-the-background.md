---
title: "チュートリアル : 操作をバックグラウンドで実行する"
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
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9be47fd57e49973c0f77a069c4f3371e4f63194
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>チュートリアル : 操作をバックグラウンドで実行する
完了に長い時間がかかる操作を実行しており、ユーザー インターフェイスで遅延が発生しないようにするには<xref:System.ComponentModel.BackgroundWorker> クラスを使用して別のスレッドで操作を実行できます。  
  
 この例で使用するコードの完全な一覧については、次を参照してください。[する方法: バック グラウンドで操作を実行](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-run-an-operation-in-the-background"></a>バック グラウンドで操作を実行するには  
  
1.  Windows フォーム デザイナーでアクティブなフォームにドラッグして 2 つ<xref:System.Windows.Forms.Button>から制御、**ツールボックス**には、フォーム、および設定、`Name`と<xref:System.Windows.Forms.Control.Text%2A>次の表に従って、ボタンのプロパティです。  
  
    |ボタン|name|テキスト|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|**Start**|  
    |`button2`|`cancelBtn`|**キャンセル**|  
  
2.  開く、**ツールボックス**をクリックして、**コンポーネント**タブをクリックし、ドラッグ、<xref:System.ComponentModel.BackgroundWorker>コンポーネントをフォームにします。  
  
     `backgroundWorker1`コンポーネントに表示されます、**コンポーネント トレイ**です。  
  
3.  **プロパティ**ウィンドウで、設定、<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティを`true`です。  
  
4.  **プロパティ**ウィンドウの**イベント**ボタンをクリックし、ダブルクリック、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベントをイベント ハンドラーを作成します。  
  
5.  時間がかかる場合にコードを挿入、<xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラー。  
  
6.  操作に必要なすべてのパラメーターを抽出、<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>パラメーター。  
  
7.  計算の結果を割り当てる、<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>です。  
  
     これができるように、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  操作の結果を取得するためのコードを挿入、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. `TimeConsumingOperation` メソッドを実装します。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. Windows フォーム デザイナーでダブルクリック`startButton`を作成する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。  
  
11. 呼び出す、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>メソッドで、<xref:System.Windows.Forms.Control.Click>イベントのハンドラーを`startButton`です。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. Windows フォーム デザイナーでダブルクリック`cancelButton`を作成する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。  
  
13. 呼び出す、<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>メソッドで、<xref:System.Windows.Forms.Control.Click>イベントのハンドラーを`cancelButton`です。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. ファイルの上部にある、System.ComponentModel および System.Threading 名前空間をインポートします。  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. ソリューションをビルド f6 キーを押してし、デバッガーの外部アプリケーションを実行するには、ctrl キーを押し-F5 キーを押します。  
  
> [!NOTE]
>  例外が発生、デバッガーでアプリケーションを実行する場合は F5 キーを押した場合、`TimeConsumingOperation`メソッドがキャッチされ、デバッガーによって表示されます。 デバッガー、外部アプリケーションを実行すると、 <xref:System.ComponentModel.BackgroundWorker> 、例外を処理し、キャッシュ内に、<xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>のプロパティ、<xref:System.ComponentModel.RunWorkerCompletedEventArgs>です。  
  
1.  をクリックして、**開始**、非同期操作を実行するボタンをクリックし、をクリックして、**キャンセル**実行中の非同期操作を停止するボタンをクリックします。  
  
     各操作の結果は、<xref:System.Windows.Forms.MessageBox> に表示されます。  
  
## <a name="next-steps"></a>次の手順  
  
-   非同期操作の進行中に進行状況を報告するフォームを実装します。 詳細については、次を参照してください。[する方法: バック グラウンド操作を使用してフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)です。  
  
-   コンポーネントの非同期パターンをサポートするクラスを実装します。 詳細については、次を参照してください。[イベント ベースの非同期パターンを実装する](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [方法: バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [方法: バックグラウンドで操作を実行する](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
