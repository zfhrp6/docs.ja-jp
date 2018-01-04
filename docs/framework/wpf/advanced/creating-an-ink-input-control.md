---
title: "インク入力コントロールの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7054728e8bf54a7cf7b71ea1224cab6a352176d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-ink-input-control"></a>インク入力コントロールの作成
カスタム コントロールを動的に作成し、インクを静的に描画します。 つまり、ユーザーは、タブレット ペンをからには、「フロー」、それ以降後のインクの表示を追加するコントロールにタブレット ペンを使用して、クリップボードから貼り付けるか、ファイルから読み込まれたを表示するインク ストロークを描画インクをレンダリングします。 インクを動的に表示するには、するために、コントロールを使用する必要があります、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>です。 静的にインクをレンダリングするには、スタイラス イベント メソッドをオーバーライドする必要があります (<xref:System.Windows.UIElement.OnStylusDown%2A>、 <xref:System.Windows.UIElement.OnStylusMove%2A>、および<xref:System.Windows.UIElement.OnStylusUp%2A>) を収集する<xref:System.Windows.Input.StylusPoint>データ、ストロークの作成に追加して、 <xref:System.Windows.Controls.InkPresenter> (がコントロール上のインクをレンダリング)。  
  
 このトピックは、次の内容で構成されています。  
  
-   [方法: スタイラス ポイント データを収集およびインク ストロークの作成](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [方法: マウスからの入力を受け入れるようにコントロールを有効にします。](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [これをまとめる](#PuttingItTogether)  
  
-   [その他のプラグインと DynamicRenderers を使用します。](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [まとめ](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>方法: スタイラス ポイント データを収集およびインク ストロークの作成  
 収集してインクを管理するコントロールを作成するには、ストロークは次の操作を行います。  
  
1.  クラスを派生<xref:System.Windows.Controls.Control>から派生したクラスのいずれかまたは<xref:System.Windows.Controls.Control>など<xref:System.Windows.Controls.Label>です。  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  追加、<xref:System.Windows.Controls.InkPresenter>をクラスに設定し、<xref:System.Windows.Controls.ContentControl.Content%2A>を新しいプロパティ<xref:System.Windows.Controls.InkPresenter>です。  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  アタッチ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>の<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.Controls.InkPresenter>を呼び出して、<xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>メソッドを追加し、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクション。 これにより、<xref:System.Windows.Controls.InkPresenter>スタイラス ポイントのデータがコントロールによって収集されたインクを表示します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  <xref:System.Windows.UIElement.OnStylusDown%2A> メソッドをオーバーライドします。  このメソッドを呼び出してスタイラスのキャプチャ<xref:System.Windows.Input.Stylus.Capture%2A>です。 コントロールが受信を続けるには、スタイラスをキャプチャして<xref:System.Windows.UIElement.StylusMove>と<xref:System.Windows.UIElement.StylusUp>スタイラスがコントロールの境界から出た場合でもイベント。 これはなく厳密に必須ですが、優れたユーザー エクスペリエンスのほとんどの場合に必要です。 新しい<xref:System.Windows.Input.StylusPointCollection>を収集する<xref:System.Windows.Input.StylusPoint>データ。 最後に、追加の初期セット<xref:System.Windows.Input.StylusPoint>にデータを<xref:System.Windows.Input.StylusPointCollection>です。  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  上書き、<xref:System.Windows.UIElement.OnStylusMove%2A>メソッドを追加し、<xref:System.Windows.Input.StylusPoint>にデータを<xref:System.Windows.Input.StylusPointCollection>先ほど作成したオブジェクト。  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  上書き、<xref:System.Windows.UIElement.OnStylusUp%2A>メソッドされ、新しい作成<xref:System.Windows.Ink.Stroke>で、<xref:System.Windows.Input.StylusPointCollection>データ。 新しい追加<xref:System.Windows.Ink.Stroke>に作成した、<xref:System.Windows.Controls.InkPresenter.Strokes%2A>のコレクション、<xref:System.Windows.Controls.InkPresenter>と解放のスタイラスをキャプチャします。  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>方法: マウスからの入力を受け入れるようにコントロールを有効にします。  
 場合は、実行、および入力デバイスとして、マウスを使用してアプリケーションに前のコントロールを追加、ストロークは保持されませんがわかります。 永続化するには、ストローク入力デバイスとして、マウスを使用すると、次の操作を行います。  
  
1.  上書き、<xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A>され、新しい作成<xref:System.Windows.Input.StylusPointCollection>イベントが発生したときに、マウスの位置を取得し、作成、<xref:System.Windows.Input.StylusPoint>ポイント データを使用して、追加、<xref:System.Windows.Input.StylusPoint>を<xref:System.Windows.Input.StylusPointCollection>です。  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  <xref:System.Windows.UIElement.OnMouseMove%2A> メソッドをオーバーライドします。 イベントが発生したときに、マウスの位置を取得し、作成、<xref:System.Windows.Input.StylusPoint>ポイント データを使用します。  追加、<xref:System.Windows.Input.StylusPoint>を<xref:System.Windows.Input.StylusPointCollection>先ほど作成したオブジェクト。  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> メソッドをオーバーライドします。  新規作成<xref:System.Windows.Ink.Stroke>で、<xref:System.Windows.Input.StylusPointCollection>データ、追加、新しい<xref:System.Windows.Ink.Stroke>に作成した、<xref:System.Windows.Controls.InkPresenter.Strokes%2A>のコレクション、<xref:System.Windows.Controls.InkPresenter>です。  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>これをまとめる  
 次の例は、カスタム コントロール、ユーザーは、マウスやペンのいずれかで使用する場合は、インクを収集します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>その他のプラグインと DynamicRenderers を使用します。  
 InkCanvas と同様に、カスタム コントロールがカスタムを持つことができます<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>および追加<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>オブジェクト。 これらは追加、<xref:System.Windows.UIElement.StylusPlugIns%2A>コレクション。 順序、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>内のオブジェクト、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>がレンダリングされるとき、インクの外観に影響します。 あると、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>と呼ばれる`dynamicRenderer`とカスタム<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>と呼ばれる`translatePlugin`タブレット ペンのインクをオフセットします。 場合`translatePlugin`最初<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>で、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>と`dynamicRenderer`2 つ目は、ユーザーがペンを移動すると、「流れ出て」、インクがオフセットされます。 場合`dynamicRenderer`は最初、および`translatePlugin`インクは、ユーザーがペンを持ち上げるまでオフセットされませんが 2 番目、します。  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>まとめ  
 収集し、スタイラス イベント メソッドをオーバーライドすることでインクをレンダリングするコントロールを作成することができます。 独自のコントロールを作成すると、派生する独自<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>クラス、およびそれらの挿入に<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>、デジタル インクで考えられるあらゆる動作を実装することができます。 アクセスがある、<xref:System.Windows.Input.StylusPoint>データが生成された、カスタマイズする機会が提供<xref:System.Windows.Input.Stylus>の入力し、し、アプリケーションの必要に応じて画面に表示します。 このような低レベルのアクセス権があるため、<xref:System.Windows.Input.StylusPoint>データ、最適なパフォーマンスで、アプリケーションのレンダリングし、インクのコレクションを実装することができます。  
  
## <a name="see-also"></a>参照  
 [高度なインク処理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [アクセスとペン入力を操作します。](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
