---
title: "方法 : カスタム コントロールからインクを選択する | Microsoft Docs"
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
  - "コントロール, インクの選択"
  - "カスタム コントロール, インクの選択"
  - "インク, 選択 (カスタム コントロールから)"
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : カスタム コントロールからインクを選択する
<xref:System.Windows.Ink.IncrementalLassoHitTester> をカスタム コントロールに追加することで、<xref:System.Windows.Controls.InkCanvas> がなげなわを使用してインクを選択するのと同様に、ユーザーがなげなわツールを使用してインクを選択できるようにコントロールを有効にすることができます。  
  
 この例は、インク対応カスタム コントロールの作成に精通していることを前提としています。  インク入力対応のカスタム コントロールを作成するには、「[インク入力コントロールの作成](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)」を参照してください。  
  
## 使用例  
 ユーザーがなげなわを描画すると、<xref:System.Windows.Ink.IncrementalLassoHitTester> は、ユーザーがなげなわを完了したときに、どのストロークがなげなわのパスの境界内に入っているかを予測します。  なげなわのパスの境界内に入っていることが特定されたストロークは、選択されているものと考えることができます。  また、選択されたストロークは、選択解除される場合もあります。  たとえば、ユーザーがなげなわを描画しながら方向を反転させた場合、<xref:System.Windows.Ink.IncrementalLassoHitTester> は、一部のストロークを選択解除します。  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester> は <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> イベントを発生させ、ユーザーがなげなわを描画している間でも、カスタム コントロールが応答できるようにします。  たとえば、ユーザーの選択および選択解除に合わせて、ストロークの外観を変更することができます。  
  
## インク モードの管理  
 コントロール上でなげなわとインクが異なって表示されると、ユーザーにとって便利です。  これを実現するには、ユーザーがインクを書き込んでいるのか選択しているのかを、カスタム コントロールが追跡する必要があります。  このような動作を実行する最も簡単な方法は、2 つの値を持つ列挙体を宣言することです。1 つはユーザーがインクを書き込んでいることを示し、もう 1 つはユーザーがインクを選択していることを示します。  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 次に、2 つの <xref:System.Windows.Ink.DrawingAttributes> をクラスに追加します。1 つはユーザーがインクを書き込んでいる場合に使用し、もう 1 つはユーザーがインクを選択している場合に使用します。  コンストラクターで <xref:System.Windows.Ink.DrawingAttributes> を初期化し、両方の <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> イベントを同じイベント ハンドラーに結合します。  次に、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> の <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> プロパティを、インクの <xref:System.Windows.Ink.DrawingAttributes> に設定します。  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 選択モードを公開するプロパティを追加します。  ユーザーが選択モードを変更したら、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> の <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> プロパティを適切な <xref:System.Windows.Ink.DrawingAttributes> オブジェクトに設定し、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> プロパティを <xref:System.Windows.Controls.InkPresenter> に再度結び付けます。  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 <xref:System.Windows.Ink.DrawingAttributes> をプロパティとして公開し、アプリケーションがインク ストロークおよび選択ストロークの外観を決定できるようにします。  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 <xref:System.Windows.Ink.DrawingAttributes> オブジェクトのプロパティが変更された場合は、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> を <xref:System.Windows.Controls.InkPresenter> に再度結び付ける必要があります。  <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> イベントのイベント ハンドラーで、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> を <xref:System.Windows.Controls.InkPresenter> に再度結び付けます。  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## IncrementalLassoHitTester の使用  
 選択されたストロークを含む <xref:System.Windows.Ink.StrokeCollection> を作成および初期化します。  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 ユーザーが、インクまたはなげなわのいずれかのストロークの描画を開始したら、選択されている任意のストロークを選択解除します。  次に、ユーザーがなげなわを描画している場合は、<xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A> を呼び出して <xref:System.Windows.Ink.IncrementalLassoHitTester> を作成し、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> イベントにサブスクライブして、<xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A> を呼び出します。  このコードは独立したメソッドとして、<xref:System.Windows.UIElement.OnStylusDown%2A> および <xref:System.Windows.UIElement.OnMouseDown%2A> メソッドから呼び出すことができます。  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 ユーザーがなげなわを描画している間に、スタイラス ポイントを <xref:System.Windows.Ink.IncrementalLassoHitTester> に追加します。  次のメソッドを、<xref:System.Windows.UIElement.OnStylusMove%2A>、<xref:System.Windows.UIElement.OnStylusUp%2A>、<xref:System.Windows.UIElement.OnMouseMove%2A>、<xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> の各メソッドから呼び出します。  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 ユーザーがストロークを選択および選択解除したときに、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=fullName> イベントを処理して応答します。  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> クラスには <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> および <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> プロパティが用意されており、それぞれ選択および選択解除されたストロークを取得します。  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 ユーザーがなげなわの描画を完了したら、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> イベントからサブスクライブを解除し、<xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A> を呼び出します。  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## すべての要素を取り入れる  
 次の例は、ユーザーがなげなわを使用してインクを選択できるようにするカスタム コントロールを示しています。  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## 参照  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>   
 <xref:System.Windows.Ink.StrokeCollection>   
 <xref:System.Windows.Input.StylusPointCollection>   
 [インク入力コントロールの作成](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)