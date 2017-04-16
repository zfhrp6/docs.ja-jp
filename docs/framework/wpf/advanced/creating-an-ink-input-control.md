---
title: "インク入力コントロールの作成 | Microsoft Docs"
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
  - "収集 (インク ストロークを)"
  - "DynamicRenderer オブジェクト"
  - "インク入力コントロール"
  - "インク ストローク, 収集"
  - "インク ストローク, 管理"
  - "インク, 描画"
  - "入力 (マウスから), 受け入れ"
  - "管理 (インク ストロークを)"
  - "マウス入力, 受け入れ"
  - "レンダリング インク"
  - "StylusPlugIn オブジェクト"
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# インク入力コントロールの作成
インクのレンダリングを動的にも静的にも行うカスタム コントロールを作成できます。  つまり、ユーザーがストロークを描画したときに、タブレット ペンから "流れる" ようにインクが表示されるようにインクをレンダリングしたり、タブレット ペンからの入力、クリップボードからの貼り付け、ファイルからの読み込みのいずれかによってインクをコントロールに追加した後にそのインクを表示したりします。  インクを動的にレンダリングするには、コントロールが <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> を使用する必要があります。  インクを静的にレンダリングするには、スタイラス イベント メソッド \(<xref:System.Windows.UIElement.OnStylusDown%2A>、<xref:System.Windows.UIElement.OnStylusMove%2A>、および <xref:System.Windows.UIElement.OnStylusUp%2A>\) をオーバーライドして、<xref:System.Windows.Input.StylusPoint> データの収集、ストロークの作成、これらのメソッドの \(コントロール上でインクをレンダリングする\) <xref:System.Windows.Controls.InkPresenter> への追加を行う必要があります。  
  
 このトピックは、次の内容で構成されています。  
  
-   [方法 : スタイラス ポイント データを収集してインク ストロークを作成する](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [方法 : コントロールでマウスからの入力を受け付けられるようにする](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [スタイラスおよびマウス双方からの入力](#PuttingItTogether)  
  
-   [追加のプラグインと DynamicRenderer の使用](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [まとめ](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## 方法 : スタイラス ポイント データを収集してインク ストロークを作成する  
 インク ストロークを収集して管理するコントロールを作成するには、次の手順を実行します。  
  
1.  <xref:System.Windows.Controls.Control> のクラス、または <xref:System.Windows.Controls.Control> の派生クラスのいずれか \(<xref:System.Windows.Controls.Label> など\) を派生します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  <xref:System.Windows.Controls.InkPresenter> をそのクラスに追加し、<xref:System.Windows.Controls.ContentControl.Content%2A> プロパティを新しい <xref:System.Windows.Controls.InkPresenter> に設定します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> メソッドを呼び出して <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> の <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> を <xref:System.Windows.Controls.InkPresenter> に割り当て、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> を <xref:System.Windows.UIElement.StylusPlugIns%2A> コレクションに追加します。  これにより、コントロールによってスタイラス ポイント データが収集されたとおりに <xref:System.Windows.Controls.InkPresenter> がインクを表示できるようになります。  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  <xref:System.Windows.UIElement.OnStylusDown%2A> メソッドをオーバーライドします。  このメソッドでは、<xref:System.Windows.Input.Stylus.Capture%2A> を呼び出してスタイラスをキャプチャします。  スタイラスをキャプチャすることにより、コントロールは、スタイラスがコントロールの境界を離れても <xref:System.Windows.UIElement.StylusMove> イベントおよび <xref:System.Windows.UIElement.StylusUp> イベントを継続して受け取ります。  これは、厳密には必須ではありませんが、快適なユーザー エクスペリエンスのためには、たいてい必要です。  新しい <xref:System.Windows.Input.StylusPointCollection> を作成し、<xref:System.Windows.Input.StylusPoint> データを収集します。  最後に、<xref:System.Windows.Input.StylusPoint> データの最初のセットを <xref:System.Windows.Input.StylusPointCollection> に追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  <xref:System.Windows.UIElement.OnStylusMove%2A> メソッドをオーバーライドし、<xref:System.Windows.Input.StylusPoint> データを、作成しておいた <xref:System.Windows.Input.StylusPointCollection> オブジェクトに追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  <xref:System.Windows.UIElement.OnStylusUp%2A> メソッドをオーバーライドし、<xref:System.Windows.Input.StylusPointCollection> データを持つ新しい <xref:System.Windows.Ink.Stroke> を作成します。  作成した新しい <xref:System.Windows.Ink.Stroke> を <xref:System.Windows.Controls.InkPresenter> の <xref:System.Windows.Controls.InkPresenter.Strokes%2A> コレクションに追加し、スタイラス キャプチャを解放します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## 方法 : コントロールでマウスからの入力を受け付けられるようにする  
 前の例で作成したコントロールをアプリケーションに追加して実行した場合に、マウスを入力デバイスとして使用すると、ストロークが永続化されないことがわかります。  マウスを入力デバイスとして使用する場合にもストロークを永続化するには、次の手順を実行します。  
  
1.  <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> をオーバーライドし、新しい <xref:System.Windows.Input.StylusPointCollection> を作成します。イベント発生時のマウスの位置を取得し、そのポイント データを使用して <xref:System.Windows.Input.StylusPoint> を作成して、その <xref:System.Windows.Input.StylusPoint> を <xref:System.Windows.Input.StylusPointCollection> に追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  <xref:System.Windows.UIElement.OnMouseMove%2A> メソッドをオーバーライドします。  イベント発生時のマウスの位置を取得し、そのポイント データを使用して <xref:System.Windows.Input.StylusPoint> を作成します。  <xref:System.Windows.Input.StylusPoint> を作成しておいた <xref:System.Windows.Input.StylusPointCollection> オブジェクトに追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> メソッドをオーバーライドします。  <xref:System.Windows.Input.StylusPointCollection> データを持つ新しい <xref:System.Windows.Ink.Stroke> を作成し、作成したその新しい <xref:System.Windows.Ink.Stroke> を <xref:System.Windows.Controls.InkPresenter> の <xref:System.Windows.Controls.InkPresenter.Strokes%2A> コレクションに追加します。  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## スタイラスおよびマウス双方からの入力  
 ユーザーがマウスまたはペンのいずれかを使用した場合にインクを収集するカスタム コントロールの例を次に示します。  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## 追加のプラグインと DynamicRenderer の使用  
 InkCanvas と同様に、カスタム コントロールでも、カスタム <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> オブジェクトや追加の <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> オブジェクトを使用できます。  これらのオブジェクトを <xref:System.Windows.UIElement.StylusPlugIns%2A> コレクションに追加します。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 内での <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> オブジェクトの順番は、インクが描画されるときの外観に影響します。  たとえば、`dynamicRenderer` という <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> およびタブレット ペンのインクをオフセットする `translatePlugin` というカスタムの <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> があるとします。  `translatePlugin` が <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 内の最初の <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> で、`dynamicRenderer` が 2 番目の場合、ユーザーがペンを動かすと、"流れる" インクがオフセットされます。  `dynamicRenderer` が最初で、`translatePlugin` が 2 番目の場合、インクは、ユーザーがペンを持ち上げるまでオフセットされません。  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## まとめ  
 スタイラス イベント メソッドのオーバーライドにより、インクを収集してレンダリングするカスタム コントロールを作成できます。  独自のコントロールを作成し、独自の <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> クラスを派生させ、それらのクラスを <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> に挿入することにより、デジタル インクで想定できるすべての動作を事実上実装できます。  生成されたとおりの <xref:System.Windows.Input.StylusPoint> データにアクセスできるため、アプリケーションの必要に応じて <xref:System.Windows.Input.Stylus> 入力をカスタマイズし、画面上にレンダリングすることができるようになります。  <xref:System.Windows.Input.StylusPoint> データにそのように低いレベルでアクセスできるため、インク コレクションの実装とアプリケーションに最適なパフォーマンスでのレンダリングを実現できます。  
  
## 参照  
 [高度なインク処理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)   
 [Accessing and Manipulating Pen Input \(ペン入力のアクセスと操作\)](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)