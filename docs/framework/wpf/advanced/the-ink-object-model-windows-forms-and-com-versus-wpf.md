---
title: 'インク オブジェクト モデル : Windows フォームおよび COM と WPF の比較'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 06a2c2049ec7fe7046bd6dae2711fe8e46592fcf
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>インク オブジェクト モデル : Windows フォームおよび COM と WPF の比較

デジタル インクをサポートする 3 つのプラットフォーム基本的には: タブレット PC の Windows フォーム プラットフォーム、Tablet PC COM プラットフォームおよび Windows Presentation Foundation (WPF) プラットフォームです。  Windows フォーム アプリケーションおよび COM プラットフォーム共有の類似のオブジェクト モデルが、オブジェクト モデル、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プラットフォームは大幅に異なります。  1 つのオブジェクト モデルに協力する開発者が理解、他の改善できるように簡単に説明する違いについて説明します。  
  
## <a name="enabling-ink-in-an-application"></a>アプリケーションでのインクを有効にします。  
 3 つすべてのプラットフォームでは、オブジェクトやタブレット ペンから入力を受信するアプリケーションを有効にするコントロールを出荷します。  Windows フォームおよび COM プラットフォームで同梱[Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx)、 [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx)、 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)と[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)クラスです。  [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx)と[Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx)追加できるコントロールは、インクを収集するのには、アプリケーションにします。  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)と[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)インクを有効にするウィンドウとカスタム コントロールを既存のウィンドウにアタッチできます。  
  
 WPF のプラットフォームが含まれています、<xref:System.Windows.Controls.InkCanvas>コントロール。  追加することができます、<xref:System.Windows.Controls.InkCanvas>をアプリケーションにし、インクを直ちに収集を開始します。 <xref:System.Windows.Controls.InkCanvas>ユーザーは、コピー、選択、およびインクのサイズを変更します。  他のコントロールを追加することができます、 <xref:System.Windows.Controls.InkCanvas>、し、ユーザーが、これらのコントロールをすぎる手書きことができます。  追加することで、インクが有効なカスタム コントロールを作成することができます、<xref:System.Windows.Controls.InkPresenter>およびそのスタイラス ポイントを収集します。  
  
 次の表は、アプリケーションでのインクを有効にする方法の詳細については、場所。  
  
|これを行う.|WPF のプラットフォームにしています.|Windows フォームや COM プラットフォームでしています.|  
|-----------------|--------------------------|------------------------------------------|  
|アプリケーションにインクが有効なコントロールを追加します。|参照してください[インクの概要](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md)です。|参照してください[自動要求フォームのサンプル](http://msdn.microsoft.com/bec4333a-62ca-4254-a39b-04bc2c556992)|  
|カスタム コントロールでインクを有効にします。|参照してください[入力コントロールをインクを作成する](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)です。|参照してください[クリップボードのサンプルのインク](http://msdn.microsoft.com/a0c42f1c-543d-44f8-83d9-fe810de410ff)です。|  
  
## <a name="ink-data"></a>インク データ  
 Windows フォームと COM プラットフォームでは、 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)、 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)、 [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx)、および[Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx)各公開、 [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType)オブジェクト。 [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx)オブジェクトは、1 つまたは複数のデータを含む[Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType)オブジェクトおよび共通のメソッドとプロパティを管理し、それらのストロークの操作を公開します。  [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx)オブジェクトが含まれている; ストロークの有効期間を管理、 [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx)オブジェクトを作成および所有するストロークを削除します。  各[Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx)親内で一意の識別子を持つ[Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx)オブジェクト。  
  
 WPF のプラットフォームで、<xref:System.Windows.Ink.Stroke?displayProperty=nameWithType>クラスが所有し、独自の有効期間を管理します。 グループ<xref:System.Windows.Ink.Stroke>でオブジェクトをまとめて収集したり、 <xref:System.Windows.Ink.StrokeCollection>、するメソッドを提供の一般的なインクのデータ管理操作など、ヒット テスト、消去、変換、および、インクをシリアル化します。 A <xref:System.Windows.Ink.Stroke> 0、1 つ、以上に所属できる<xref:System.Windows.Ink.StrokeCollection>どのオブジェクトが時間を確保できるようにします。  代わりに、 [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType)オブジェクト、<xref:System.Windows.Controls.InkCanvas>と<xref:System.Windows.Controls.InkPresenter>が含まれて、<xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>です。  
  
 次の図のペアでは、データのインク オブジェクト モデルを比較します。  Windows フォームや COM プラットフォームでは、上、 [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType)オブジェクトの有効期間の制限、 [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType)オブジェクト、および個々 のストロークに属しているスタイラス パケットです。  2 つ以上のストロークを参照できる同じ[Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType)オブジェクトを次の図に示すようにします。  
  
 ![COM のインク オブジェクト モデルのダイアグラム&#47;Winforms です。] (../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、各<xref:System.Windows.Ink.Stroke?displayProperty=nameWithType>がある限り問題への参照が存在する共通言語ランタイム オブジェクト。  各<xref:System.Windows.Ink.Stroke>参照、<xref:System.Windows.Input.StylusPointCollection>と<xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType>オブジェクトも、共通言語ランタイム オブジェクト。  
  
 ![WPF のインク オブジェクト モデルのダイアグラム。] (../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 次の表に一般的なタスクを実行する方法の比較、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プラットフォームと Windows フォーム アプリケーションおよび COM プラットフォームです。  
  
|タスク|Windows Presentation Foundation|Windows フォーム アプリケーションおよび COM|  
|----------|-------------------------------------|---------------------------|  
|インクを保存します。|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))|  
|インクを読み込み|作成、<xref:System.Windows.Ink.StrokeCollection>で、<xref:System.Windows.Ink.StrokeCollection.%23ctor%2A>コンス トラクターです。|[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)|  
|ヒット テスト|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://msdn.microsoft.com/library/aa515934.aspx)|  
|インクをコピーします。|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)|  
|インクを貼り付けます|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)|  
|ストロークのコレクションのカスタム プロパティのアクセス|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (プロパティが内部的に保存されを使用してアクセス<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>、 <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>、および<xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|使用して[Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)|  
  
### <a name="sharing-ink-between-platforms"></a>プラットフォーム間でのインクの共有  
 プラットフォームには、インク データの別のオブジェクト モデルがありますが、プラットフォーム間でデータを共有するは非常に簡単です。 次の例では、Windows フォーム アプリケーションからインクを保存し、Windows Presentation Foundation アプリケーションにインクを読み込みます。  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 次の例では、Windows Presentation Foundation アプリケーションからインクを保存し、Windows フォーム アプリケーションにインクを読み込みます。  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>タブレット ペンからのイベント  
 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)、 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)、および[Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx)プラットフォームは Windows フォームと COM イベントを受け取るときに、ユーザーペンのデータを入力します。  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx)または[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx)ウィンドウまたはコントロールにアタッチされ、タブレットの入力データによって発生したイベントにサブスクライブできます。  これらのイベントが発生したスレッド ペン、マウスを使用して、イベントが発生したかどうかに依存するかプログラムです。  これらのイベントに関連してスレッド処理の詳細については、次を参照してください。[一般的なスレッド処理の考慮事項](http://msdn.microsoft.com/cf35724f-5f80-4b3e-992a-a9d5ea99aae9)と[スレッドでイベントが起動できる](http://msdn.microsoft.com/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f)です。  
  
 Windows Presentation Foundation のプラットフォームで、<xref:System.Windows.UIElement>クラスがイベントをペン入力します。 これは、すべてのコントロールがスタイラス イベントの完全なセットを公開することを意味します。  スタイラス イベントがイベントのトンネリング バブルを持っているペアし、アプリケーション スレッドで常に発生します。  詳細については、次を参照してください。[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)です。  
  
 次の図では、スタイラス イベントを発生させるクラスのオブジェクト モデルを比較します。 Windows Presentation Foundation のオブジェクト モデル イベントのみを表示、バブル、トンネリング イベント対応ではありません。  
  
 ![WPF と Winforms のスタイラス イベントのダイアグラム。] (../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>ペンのデータ  
 3 つすべてのプラットフォームをインターセプトし、タブレット ペンに付属しているデータを操作する方法を提供します。  Windows フォームと COM のプラットフォームで、これを実現するには、 [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx)ウィンドウまたはコントロールに、アタッチする方法、および実装するクラスを作成する、 [Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx)または[Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx)インターフェイスです。 カスタム プラグインがのプラグインのコレクションに追加し、 [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx)です。 このオブジェクト モデルの詳細については、次を参照してください。 [StylusInput Api のアーキテクチャ](http://msdn.microsoft.com/88bab0ab-df9f-4813-9a9f-9a137813f0b4)です。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 、プラットフォーム、<xref:System.Windows.UIElement>クラスは、プラグイン、設計に同様のコレクションを公開、 [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx)です。  データを受信するペンから継承するクラスを作成する<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>オブジェクトを追加して、<xref:System.Windows.UIElement.StylusPlugIns%2A>のコレクション、<xref:System.Windows.UIElement>です。 この操作の詳細については、次を参照してください。[スタイラスからの入力を傍受](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)です。  
  
 すべてのプラットフォームでは、スレッド プールは、スタイラス イベントを使用してインク データを受信し、アプリケーションのスレッドに送信します。  Windows プラットフォームでは、COM スレッド処理の詳細については、次を参照してください。 [StylusInput Api に関する考慮事項をスレッド](http://msdn.microsoft.com/5d98768a-c60b-4bb0-8640-9bf38254d41f)です。  Windows Presentation ソフトウェア スレッド処理の詳細については、次を参照してください。 [、インク スレッド処理モデル](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)です。  
  
 次の図では、ペンのスレッド プールでペンのデータを受信するクラスのオブジェクト モデルを比較します。  
  
 ![StylusPlugin モデル WPF と Winforms のダイアグラム。] (../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")
