---
title: "How to: Use Components That Support the Event-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Use Components That Support the Event-based Asynchronous Pattern
大部分のコンポーネントは、非同期的に作業を行うオプションを提供します。  たとえば、<xref:System.Media.SoundPlayer> および <xref:System.Windows.Forms.PictureBox> コンポーネントを使用すると、メイン スレッドを中断せずに実行したまま、サウンドおよびイメージを "バックグラウンド" で読み込むことができます。  
  
 サポートするクラスで非同期メソッドを使用して、他のイベントの場合と同じように [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) は場合、イベント ハンドラーをコンポーネントの *MethodName*`Completed` イベントにアタッチする簡単です。  *MethodName*`Async` のメソッドを呼び出すと、アプリケーションが *MethodName*`Completed` イベントが発生させるまで中断されずに実行されます。  イベント ハンドラーで <xref:System.ComponentModel.AsyncCompletedEventArgs> パラメーターを調べると、非同期操作が正常に完了したか、キャンセルされたかを確認できます。  
  
 イベンド ハンドラーの使用方法の詳細については、「[イベント ハンドラーの概要](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)」を参照してください。  
  
 次の手順は、<xref:System.Windows.Forms.PictureBox> コントロールの非同期イメージ読み込み機能を使用する方法を示しています。  
  
### PictureBox コントロールを有効にして、非同期的にイメージを読み込むには  
  
1.  フォームで <xref:System.Windows.Forms.PictureBox> コンポーネントのインスタンスを作成します。  
  
2.  <xref:System.Windows.Forms.PictureBox.LoadCompleted> イベントにイベント ハンドラーを割り当てます。  
  
     ここで、非同期ダウンロード中に発生したエラーを確認します。  キャンセルも確認します。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  フォームに 2 つのボタン \(`loadButton` および `cancelLoadButton`\) を追加します。  <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを追加して、ダウンロードを開始およびキャンセルします。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  アプリケーションを実行します。  
  
     イメージのダウンロードの進行中には、フォームを自由に移動、最小化、最大化できます。  
  
## 参照  
 [方法 : バックグラウンドで操作を実行する](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/ja-jp/c731a50c-09c1-4468-9646-54c86b75d269)