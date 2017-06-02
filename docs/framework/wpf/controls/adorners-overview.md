---
title: "装飾の概要 | Microsoft Docs"
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
  - "装飾 [WPF], 装飾の概要"
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# 装飾の概要
装飾は、ユーザーにビジュアル キューを提供するために使用する、特別な種類の <xref:System.Windows.FrameworkElement> です。  装飾にはさまざまな使用法があり、要素に機能ハンドルを追加したり、コントロールに関する状態情報を提供するためなどに使用できます。  
  
   
  
<a name="about_Adorners"></a>   
## 装飾について  
 <xref:System.Windows.Documents.Adorner> は、<xref:System.Windows.UIElement> にバインドされるカスタム <xref:System.Windows.FrameworkElement> です。  装飾は、<xref:System.Windows.Documents.AdornerLayer> に描画されます。これは、常に装飾対象の要素またはそのコレクションの上に存在するレンダリング サーフェイスです。  装飾の描画は、その装飾がバインドされる <xref:System.Windows.UIElement> の描画とは独立して実行されます。  通常、装飾は、装飾対象の要素の左上に位置する標準の 2\-D 座標の原点を使用して、バインド先の要素に対して相対的な位置に配置されます。  
  
 装飾の一般的な用途には、以下が含まれます。  
  
-   ユーザーが要素を何らかの方法で操作 \(サイズ変更、回転、位置変更など\) できるようにする機能ハンドルを <xref:System.Windows.UIElement> に追加する。  
  
-   さまざまな状態を示すために、または各種のイベントへの対応として、視覚的フィードバックを提供する。  
  
-   <xref:System.Windows.UIElement> に視覚的装飾をオーバーレイする。  
  
-   <xref:System.Windows.UIElement> の一部または全部を視覚的にマスクまたはオーバーライドする。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、ビジュアル要素を装飾するための基本的なフレームワークを提供します。  オブジェクトを装飾する際に使用する主なクラスと、その用途の一覧を次の表に示します。  その後に、いくつかの使用方法の例を示します。  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|すべての具体的な装飾の実装の継承元になる抽象基本クラス。|  
|<xref:System.Windows.Documents.AdornerLayer>|装飾される 1 つ以上の要素について、装飾のレンダリング層を表すクラス。|  
|<xref:System.Windows.Documents.AdornerDecorator>|1 つの装飾層を要素のコレクションに関連付けることを可能にするクラス。|  
  
<a name="implement_custom_Adorner"></a>   
## カスタム装飾を実装する  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が提供する装飾フレームワークは、カスタム装飾の作成をサポートすることを主な目的としています。  抽象型 <xref:System.Windows.Documents.Adorner> クラスから継承されるクラスを実装することにより、カスタムの Adorner が作成されます。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Adorner> の親は、装飾される要素ではなく、<xref:System.Windows.Documents.Adorner> を描画する <xref:System.Windows.Documents.AdornerLayer> です。  
  
 簡単な装飾を実装するクラスを次の例に示します。  この例の装飾は、<xref:System.Windows.UIElement> の四隅を円で装飾します。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <xref:System.Windows.Controls.TextBox> に適用された SimpleCircleAdorner を次の図に示します。  
  
 ![装飾の例: 装飾された TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")  
  
<a name="rendering_behavior_for_Adorners"></a>   
## 装飾のレンダリング動作  
 Adorner 自体には継承されたレンダリング動作は含まれず、Adorner のレンダリングは Adorner の実装者の責任で行う必要がある点について注意が必要です。  レンダリング動作を実装する一般的な方法としては、<xref:System.Windows.UIElement.OnRender%2A> メソッドをオーバーライドし、1 つ以上の <xref:System.Windows.Media.DrawingContext> オブジェクトを使用して、装飾のビジュアルを必要に応じて描画します \(上の例を参照\)。  
  
> [!NOTE]
>  装飾層に配置されているすべてのものは、設定した他のすべてのスタイルの上に描画されます。  つまり、装飾は常に視覚的に最上位にあり、[z オーダー](GTMT)を使用してオーバーライドすることはできません。  
  
<a name="adorner_events_hittest"></a>   
## イベントおよびヒット テスト  
 他のすべての <xref:System.Windows.FrameworkElement> と同様に、装飾も入力イベントを受け取ります。  装飾は、それが装飾する要素よりも常に高い [z オーダー](GTMT)を持つため、下位にある装飾対象の要素に向けられた入力イベント \(たとえば <xref:System.Windows.UIElement.Drop> や <xref:System.Windows.UIElement.MouseMove>\) であっても受け取ります。  装飾は、特定の入力イベントをリッスンし、それらのイベントを再び発生させることによって下位にある装飾対象の要素に渡すことができます。  
  
 装飾を通過させてその下にある要素のヒット テストを有効にするには、その装飾でヒット テストの <xref:System.Windows.UIElement.IsHitTestVisible%2A> プロパティを **false** に設定します。  ヒット テストの詳細については、次を参照してください。  
  
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## 単一の UIElement を装飾する  
 Adorner を特定の <xref:System.Windows.UIElement> にバインドするには、次の手順を実行します。  
  
1.  静的メソッド <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> を呼び出し、修飾対象の <xref:System.Windows.UIElement> の <xref:System.Windows.Documents.AdornerLayer> オブジェクトを取得します。  <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> は、指定した <xref:System.Windows.UIElement> を起点にしてビジュアル ツリーを上方向に検索し、最初に見つかった修飾層を返します。  \(Adorner のレイヤーが見つからない場合は、メソッドにより null が返されます。\)  
  
2.  <xref:System.Windows.Documents.AdornerLayer.Add%2A> メソッドを呼び出し、装飾を対象の <xref:System.Windows.UIElement> にバインドします。  
  
 次の例では、SimpleCircleAdorner \(前述\) を <xref:System.Windows.Controls.TextBox> \(名前は *myTextBox*\) にバインドしています。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Adorner を別の要素にバインドするために [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用することは、現在サポートされていません。  
  
<a name="adorn_children_panel"></a>   
## パネルの子を装飾する  
 Adorner を <xref:System.Windows.Controls.Panel> の子にバインドするには、次の手順を実行します。  
  
1.  `静的`メソッド <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> を呼び出し、子が装飾の対象となる要素の装飾層を検出します。  
  
2.  親要素の子を列挙し、<xref:System.Windows.Documents.AdornerLayer.Add%2A> メソッドを呼び出して Adorner を各子要素にバインドします。  
  
 次の例では、SimpleCircleAdorner \(前述\) を <xref:System.Windows.Controls.StackPanel> の子 \(名前は *myStackPanel*\) にバインドしています。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## 参照  
 <xref:System.Windows.Media.AdornerHitTestResult>   
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)