---
title: '方法 : イベントベースの非同期パターンをサポートするコンポーネントを使用する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: f0bf9b1da76033ef40cc72657ee722083a6f8b1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>方法 : イベントベースの非同期パターンをサポートするコンポーネントを使用する
多くのコンポーネントでは、非同期的に作業を実行するオプションが提供されます。 たとえば、<xref:System.Media.SoundPlayer> と <xref:System.Windows.Forms.PictureBox> コンポーネントでは、メイン スレッドが中断されることなく、実行され続ける間に、"バックグラウンドで" 音声とイメージを読み込むことができます。  
  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)をサポートするクラスで非同期メソッドを使用することは、別のイベントに対して行うように、イベント ハンドラーをコンポーネントの *MethodName***Completed** イベントにアタッチするのと同じくらい単純です。 *MethodName***Async** メソッドを呼び出すと、*MethodName***Completed** イベントが発生するまで、アプリケーションは中断されることなく実行され続けます。 イベント ハンドラーで、非同期操作が正常に完了するか、キャンセルされたかどうかを判断するには、<xref:System.ComponentModel.AsyncCompletedEventArgs> パラメーターを調べることができます。  
  
 イベント ハンドラーの使用に関する詳細については、「[イベント ハンドラーの概要](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)」を参照してください。  
  
 次の手順は、<xref:System.Windows.Forms.PictureBox> コントロールの非同期イメージ読み込み機能を使用する方法について示しています。  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>イメージを非同期的に読み込むために PictureBox コントロールを有効にするには  
  
1.  フォームで <xref:System.Windows.Forms.PictureBox> コンポーネントのインスタンスを作成します。  
  
2.  イベント ハンドラーを <xref:System.Windows.Forms.PictureBox.LoadCompleted> イベントに割り当てます。  
  
     非同期ダウンロード中に発生する可能性があるエラーをここで確認してください。 また、ここはキャンセルを確認するための場所でもあります。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  `loadButton` と `cancelLoadButton` と呼ばれる 2 つのボタンをフォームに追加します。 ダウンロードの開始とキャンセルを行うために、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーを追加します。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  アプリケーションを実行します。  
  
     イメージのダウンロードを進めるときに、フォームを自由に移動したり、最小化や最大化を行ったりすることができます。  
  
## <a name="see-also"></a>参照  
 [方法: バックグラウンドで操作を実行する](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [ビルド内にありません: Visual Basic でのマルチスレッド](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)
