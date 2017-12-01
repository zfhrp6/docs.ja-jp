---
title: "方法 : イベントベースの非同期パターンをサポートするコンポーネントを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49e03a8d886ccd4ed6e4b2a19692c1874f5928ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>方法 : イベントベースの非同期パターンをサポートするコンポーネントを使用する
多くのコンポーネントは、その作業を非同期的に実行した場合のオプションを提供します。 <xref:System.Media.SoundPlayer>と<xref:System.Windows.Forms.PictureBox>コンポーネント、たとえば、サウンドをロードして、メイン スレッドが中断されることがなく実行を止めずに"バック グラウンド"でイメージを有効にします。  
  
 非同期メソッドをサポートするクラスを使用して、 [- イベント ベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)簡単に、コンポーネントのイベント ハンドラーをアタッチするのには、 *MethodName* `Completed`イベントだけ、他のイベントの場合と同様です。 呼び出すと、 *MethodName* `Async`メソッド、アプリケーションは引き続き実行するまで中断することがなく、 *MethodName* `Completed`イベントが発生します。 イベント ハンドラーで確認することができます、<xref:System.ComponentModel.AsyncCompletedEventArgs>パラメーター、非同期操作が正常に完了した場合、またはが取り消された場合を判断します。  
  
 詳細については、イベント ハンドラーを使用して、次を参照してください。[イベント ハンドラーの概要](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)です。  
  
 次の手順の非同期のイメージの読み込み機能を使用する方法を示しています、<xref:System.Windows.Forms.PictureBox>コントロール。  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>イメージを非同期的にロードする PictureBox コントロールを有効にするには  
  
1.  インスタンスを作成、<xref:System.Windows.Forms.PictureBox>コンポーネントをフォームでします。  
  
2.  イベント ハンドラーを割り当てます、<xref:System.Windows.Forms.PictureBox.LoadCompleted>イベント。  
  
     ここで、非同期のダウンロード中に発生したエラーを確認します。 これは、キャンセルをチェックする場所。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  呼ばれる 2 つのボタンの追加`loadButton`と`cancelLoadButton`フォームにします。 追加<xref:System.Windows.Forms.Control.Click>イベント ハンドラーを起動し、ダウンロードをキャンセルします。  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  アプリケーションを実行します。  
  
     イメージのダウンロードが進むにつれては、フォームを自由に移動して最小化、および最大化できます。  
  
## <a name="see-also"></a>関連項目  
 [方法: バックグラウンドで操作を実行する](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NOT IN BUILD: Visual Basic でのマルチ スレッド](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)
