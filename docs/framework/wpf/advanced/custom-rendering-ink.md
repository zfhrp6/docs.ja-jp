---
title: "カスタム レンダリング インク | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "クラス, DynamicRenderer"
  - "クラス, InkCanvas"
  - "クラス, ストローク"
  - "カスタム レンダリング インク"
  - "DynamicRenderer クラス"
  - "インク, カスタム レンダリング"
  - "InkCanvas クラス"
  - "Stroke クラス"
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# カスタム レンダリング インク
ストロークの <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> プロパティを使用すると、ストロークのサイズ、色、形状などの外観を指定できますが、<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> で可能な指定以上の外観にカスタマイズする必要が生じる場合もあります。  インクの外観は、エアブラシや油絵の具などのさまざまな効果の外観でレンダリングすることでカスタマイズできます。  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] では、カスタムの <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> オブジェクトと <xref:System.Windows.Ink.Stroke> オブジェクトを実装することで、インクのカスタム レンダリングを実行できます。  
  
 このトピックは、次の内容で構成されています。  
  
-   [アーキテクチャ](#Architecture)  
  
-   [動的レンダラーの実装](#ImplementingADynamicRenderer)  
  
-   [Implementing a Custom Stroke](#ImplementingACustomStroke)  
  
-   [カスタム InkCanvas の実装](#ImplementingACustomInkCanvas)  
  
-   [まとめ](#Conclusion)  
  
<a name="Architecture"></a>   
## アーキテクチャ  
 インクのレンダリングは 2 回行われます。ユーザーがインクをインク サーフェイスに書き込んだときと、ストロークがインク対応サーフェイスに追加された後です。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> はユーザーがタブレット ペンをデジタイザー上で動かしたときにインクをレンダリングし、<xref:System.Windows.Ink.Stroke> は要素に追加されたときにレンダリングされます。  
  
 インクを動的にレンダリングするときに実装するクラスは 3 つあります。  
  
1.  **DynamicRenderer** : <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> から派生するクラスを実装します。  このクラスは、ストロークを描画されたとおりにレンダリングする特殊な <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> です。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> は個別のスレッドでレンダリングを実行するため、アプリケーションのユーザー インターフェイス \(UI\) スレッドがブロックされても、インクを収集するためにインク サーフェイスが表示されます。  スレッド処理モデルの詳細については、「[インク スレッド モデル](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)」を参照してください。  ストロークの動的レンダリングをカスタマイズするには、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> メソッドをオーバーライドします。  
  
2.  **Stroke** : <xref:System.Windows.Ink.Stroke> から派生するクラスを実装します。  このクラスは、<xref:System.Windows.Input.StylusPoint> データが <xref:System.Windows.Ink.Stroke> オブジェクトに変換された後に、そのデータの静的レンダリングを実行します。  ストロークの静的レンダリングが動的レンダリングと一貫するようにするには、<xref:System.Windows.Ink.Stroke.DrawCore%2A> メソッドをオーバーライドします。  
  
3.  **InkCanvas** : <xref:System.Windows.Controls.InkCanvas> から派生するクラスを実装します。  カスタマイズされた <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> を <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> プロパティに割り当てます。  <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> メソッドをオーバーライドし、カスタム ストロークを <xref:System.Windows.Controls.InkCanvas.Strokes%2A> プロパティに追加します。  これにより、インクの外観の一貫性が確保されます。  
  
<a name="ImplementingADynamicRenderer"></a>   
## 動的レンダラーの実装  
 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> クラスは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の標準クラスですが、特殊なレンダリングを実行するには、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> から派生したカスタマイズ動的レンダラーを作成し、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> メソッドをオーバーライドする必要があります。  
  
 線形グラデーション ブラシ効果を使用してインクを描画するカスタマイズされた <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> の例を次に示します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## カスタム ストロークの実装  
 <xref:System.Windows.Ink.Stroke> から派生するクラスを実装します。  このクラスは、<xref:System.Windows.Input.StylusPoint> データが <xref:System.Windows.Ink.Stroke> オブジェクトに変換された後に、そのデータのレンダリングを実行します。  実際の描画を実行するには、<xref:System.Windows.Ink.Stroke.DrawCore%2A> クラスをオーバーライドします。  
  
 <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> メソッドを使用して、Stroke クラスにカスタム データを格納することもできます。  このデータは、永続化される場合、ストローク データと共に格納されます。  
  
 <xref:System.Windows.Ink.Stroke> クラスは、ヒット テストを実行することもできます。  また、現在のクラスで <xref:System.Windows.Ink.Stroke.HitTest%2A> メソッドをオーバーライドして、独自のヒット テスト アルゴリズムを実装することもできます。  
  
 次の C\# のコードは、<xref:System.Windows.Input.StylusPoint> データを 3\-D ストロークとしてレンダリングするカスタムの <xref:System.Windows.Ink.Stroke> クラスを示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## カスタム InkCanvas の実装  
 カスタマイズされた <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> およびストロークの最も簡単な使用方法は、<xref:System.Windows.Controls.InkCanvas> から派生するクラスを実装して使用することです。  <xref:System.Windows.Controls.InkCanvas> には、ユーザーがストロークを描画しているときにそのストロークをどのようにレンダリングするかを指定する <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> プロパティがあります。  
  
 <xref:System.Windows.Controls.InkCanvas> でストロークのカスタム レンダリングを行うには、次の操作を実行します。  
  
-   <xref:System.Windows.Controls.InkCanvas> から派生するクラスを作成します。  
  
-   カスタマイズされた <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> を <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=fullName> プロパティに割り当てます。  
  
-   <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> メソッドをオーバーライドします。  このメソッドで、InkCanvas に追加された元のストロークを削除します。  次に、カスタム ストロークを作成して <xref:System.Windows.Controls.InkCanvas.Strokes%2A> プロパティに追加し、カスタム ストロークを含む新しい <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> を使用して基本クラスを呼び出します。  
  
 次の C\# のコードは、カスタマイズされた <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> を使用してカスタム ストロークを収集するカスタムの <xref:System.Windows.Controls.InkCanvas> クラスを示しています。  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas> には、複数の <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> を追加できます。  複数の <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> オブジェクトを <xref:System.Windows.Controls.InkCanvas> に追加するには、それらのオブジェクトを <xref:System.Windows.UIElement.StylusPlugIns%2A> プロパティに追加します。  
  
<a name="Conclusion"></a>   
## まとめ  
 インクの外観をカスタマイズするには、独自の <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、<xref:System.Windows.Ink.Stroke>、および <xref:System.Windows.Controls.InkCanvas> クラスを派生させます。  これらのクラスを合わせて、ユーザーがストロークを描画したときとそのストロークが収集された後のストロークの外観の一貫性を確保することができます。  
  
## 参照  
 [高度なインク処理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)