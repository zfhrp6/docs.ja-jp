---
title: カスタム レンダリング インク
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: 2c627f757c1eccc37f57aea6880ffc8a362e5ddb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540434"
---
# <a name="custom-rendering-ink"></a>カスタム レンダリング インク
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>ストロークのプロパティでは、そのサイズ、色、および図形など、線の外観を指定することができますが、機能の外観をカスタマイズすることもあります<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>を許可します。 エアブラシ、油絵、およびその他の多くの効果の外観でレンダリングすることで、インクの外観をカスタマイズしたい場合もあります。 Windows Presentation Foundation (WPF) により、カスタムを実装することでインクをレンダリングすると、カスタム<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>と<xref:System.Windows.Ink.Stroke>オブジェクト。  
  
 このトピックは、次の内容で構成されています。  
  
-   [アーキテクチャ](#Architecture)  
  
-   [動的なレンダラーの実装](#ImplementingADynamicRenderer)  
  
-   [カスタム ストロークの実装](#ImplementingCustomStrokes)  
  
-   [カスタム InkCanvas の実装](#ImplementingACustomInkCanvas)  
  
-   [まとめ](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>アーキテクチャ  
 インク レンダリングは 2 回発生します。ユーザーがインクを手描き入力サーフェイスに書き込む時と、ストロークが手書き対応のサーフェスに追加された後です。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 、ユーザーは、デジタイザー上でタブレット ペンを動かすと、インクをレンダリングおよび<xref:System.Windows.Ink.Stroke>要素に追加すること自体を表示します。  
  
 インクを動的にレンダリングするときに実装する 3 つのクラスがあります。  
  
1.  **DynamicRenderer**: から派生するクラスを実装する<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>です。 このクラスは、特殊な<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>表示するための線が描画されるとします。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>アプリケーション ユーザー インターフェイス (UI) スレッドがブロックされている場合でも、インクを収集する場合は、インクの画面が表示されるように、別のスレッドでレンダリングがします。 スレッド処理モデルの詳細については、「[インク スレッド モデル](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)」を参照してください。 ストロークを動的に表示をカスタマイズするには、上書き、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>メソッドです。  
  
2.  **ストローク**: から派生するクラスを実装する<xref:System.Windows.Ink.Stroke>です。 静的表示するため、このクラスは、<xref:System.Windows.Input.StylusPoint>データに変換した後、<xref:System.Windows.Ink.Stroke>オブジェクト。 上書き、<xref:System.Windows.Ink.Stroke.DrawCore%2A>ストロークの静的なレンダリングできることを確認するメソッドは動的なレンダリングと一致します。  
  
3.  **InkCanvas:** から派生するクラスを実装する<xref:System.Windows.Controls.InkCanvas>です。 カスタマイズされた割り当てる<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>プロパティです。 上書き、<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>メソッドにカスタムの線を追加し、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>プロパティです。 これにより、インクの外観に一貫性を確保します。  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>動的なレンダラーの実装  
 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>クラスは、標準の一部の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、以上を実行するには、レンダリング特化したから派生したカスタマイズされた動的レンダラーを作成する必要があります、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>をオーバーライドし、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>メソッドです。  
  
 次の例で、カスタマイズされた<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>線形グラデーション ブラシ効果のあるインクを描画します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>カスタム ストロークの実装  
 <xref:System.Windows.Ink.Stroke> から派生するクラスを実装します。 このクラスは、レンダリング<xref:System.Windows.Input.StylusPoint>データに変換した後、<xref:System.Windows.Ink.Stroke>オブジェクト。 上書き、<xref:System.Windows.Ink.Stroke.DrawCore%2A>実際の描画を実行するクラス。  
  
 ストローク クラスを使用してカスタム データを格納も、<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>メソッドです。 このデータは、保持されるときにストローク データと共に格納されます。  
  
 <xref:System.Windows.Ink.Stroke>クラスは、ヒット テストも実行できます。 独自のヒットをオーバーライドすることでアルゴリズムをテストを実装することも、<xref:System.Windows.Ink.Stroke.HitTest%2A>現在のクラスのメソッドです。  
  
 次の c# コードをカスタムに示します<xref:System.Windows.Ink.Stroke>レンダリング クラス<xref:System.Windows.Input.StylusPoint>3-D ストロークとしてデータ。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>カスタム InkCanvas の実装  
 カスタマイズしたを使用する最も簡単な方法<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ストロークから派生するクラスを実装して<xref:System.Windows.Controls.InkCanvas>し、これらのクラスを使用します。 <xref:System.Windows.Controls.InkCanvas>が、<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>ユーザーが描画するときに、線がどのように表示されるかを指定するプロパティです。  
  
 カスタム上のストロークの表示、<xref:System.Windows.Controls.InkCanvas>次の操作します。  
  
-   派生するクラスを作成、<xref:System.Windows.Controls.InkCanvas>です。  
  
-   カスタマイズした割り当てる<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>プロパティです。  
  
-   <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> メソッドをオーバーライドします。 このメソッドで、InkCanvas に追加された元のストロークを削除します。 カスタム線を作成し、それを追加、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>プロパティ、および呼び出し、基本クラスを新しい<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>カスタム線を格納しています。  
  
 次の c# コードに示しますカスタム<xref:System.Windows.Controls.InkCanvas>を使用して、カスタマイズされたクラス<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>し、カスタムのストロークを収集します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas> 1 つ以上の<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>します。 複数を追加する<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>オブジェクトを<xref:System.Windows.Controls.InkCanvas>に追加することによって、<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティです。  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>まとめ  
 インクの外観をカスタマイズするには、独自の派生によって<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、 <xref:System.Windows.Ink.Stroke>、および<xref:System.Windows.Controls.InkCanvas>クラスです。 これらのクラスを合わせて、ユーザーがストロークを描画し、その後ストロークが収集される際に、ストロークの外観を一致させます。  
  
## <a name="see-also"></a>関連項目  
 [高度なインク処理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
