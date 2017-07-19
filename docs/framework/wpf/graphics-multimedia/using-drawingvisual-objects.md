---
title: "DrawingVisual オブジェクトの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DrawingVisual オブジェクト (ビジュアル層の)"
  - "ビジュアル層, DrawingVisual オブジェクト"
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# DrawingVisual オブジェクトの使用
ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ビジュアル層で <xref:System.Windows.Media.DrawingVisual> オブジェクトを使用する方法の概要を説明します。  
  
 このトピックは、次のセクションで構成されています。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [DrawingVisual オブジェクト](#drawing_visual_object)  
  
-   [DrawingVisual ホスト コンテナー](#drawingvisual_host_container)  
  
-   [DrawingVisual オブジェクトの作成](#creating_drawingvisual_objects)  
  
-   [FrameworkElement メンバーのオーバーライドの作成](#creating_overrides)  
  
-   [ヒット テストのサポート](#providing_hit_testing_support)  
  
-   [関連トピック](#seeAlsoToggle)  
  
<a name="drawingvisual_object"></a>   
## DrawingVisual オブジェクト  
 <xref:System.Windows.Media.DrawingVisual> は、図形、イメージ、またはテキストの描画に使用する軽量の描画クラスです。  このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないため、パフォーマンスが向上するからです。  このため、背景やクリップ アートの描画に適しています。  
  
<a name="drawingvisual_host_container"></a>   
## DrawingVisual ホスト コンテナー  
 <xref:System.Windows.Media.DrawingVisual> オブジェクトを使用するには、オブジェクトのホスト コンテナーを作成する必要があります。  ホスト コンテナー オブジェクトは、<xref:System.Windows.FrameworkElement> クラスから継承する必要があります。このクラスは、<xref:System.Windows.Media.DrawingVisual> クラスがサポートしていないレイアウトやイベント処理をサポートします。  ホスト コンテナー オブジェクトの主な目的は子オブジェクトを格納することなので、ホスト コンテナー オブジェクトには表示プロパティは表示されません。  ただし、ホスト コンテナーの <xref:System.Windows.UIElement.Visibility%2A> プロパティは、<xref:System.Windows.Visibility> に設定する必要があります。この値に設定しない場合、その子要素のいずれも表示されなくなります。  
  
 ビジュアル オブジェクトのホスト コンテナー オブジェクトを作成する場合は、<xref:System.Windows.Media.VisualCollection> にビジュアル オブジェクト参照を格納する必要があります。  <xref:System.Windows.Media.VisualCollection.Add%2A> メソッドを使用して、ビジュアル オブジェクトをホスト コンテナーに追加します。  次の例では、ホスト コンテナー オブジェクトを作成し、3 つのビジュアル オブジェクトをその <xref:System.Windows.Media.VisualCollection> に追加します。  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  前のコード例を含むコード サンプル全体については、[DrawingVisual を使用したヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159994)を参照してください。  
  
<a name="creating_drawingvisual_objects"></a>   
## DrawingVisual オブジェクトの作成  
 <xref:System.Windows.Media.DrawingVisual> オブジェクトの作成時には、オブジェクトに描画内容は含まれていません。  テキスト、グラフィックス、またはイメージ コンテンツを追加するには、オブジェクトの <xref:System.Windows.Media.DrawingContext> を取得し、そのコンテキストに描画します。  <xref:System.Windows.Media.DrawingContext> は、<xref:System.Windows.Media.DrawingVisual> オブジェクトの <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> メソッドを呼び出すことによって返されます。  
  
 <xref:System.Windows.Media.DrawingContext> に四角形を描画するには、<xref:System.Windows.Media.DrawingContext> オブジェクトの <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> メソッドを使用します。  他の種類のコンテンツを描画するための同様のメソッドがあります。  <xref:System.Windows.Media.DrawingContext> へのコンテンツの描画が完了したら、<xref:System.Windows.Media.DrawingContext.Close%2A> メソッドを呼び出して <xref:System.Windows.Media.DrawingContext> を閉じ、コンテンツを保持します。  
  
 次の例では、<xref:System.Windows.Media.DrawingVisual> オブジェクトを作成し、その <xref:System.Windows.Media.DrawingContext> に四角形を描画します。  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## FrameworkElement メンバーのオーバーライドの作成  
 ホスト コンテナー オブジェクトは、ビジュアル オブジェクトのコレクションを管理します。  このため、ホスト コンテナーは派生 <xref:System.Windows.FrameworkElement> クラスのメンバー オーバーライドを実装する必要があります。  
  
 オーバーライドする必要がある 2 つのメンバーを次に示します。  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A> : 子要素のコレクションから指定したインデックス位置にある子を返します。  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A> : この要素内の子ビジュアル要素の数を取得します。  
  
 次の例では、2 つの <xref:System.Windows.FrameworkElement> メンバーのオーバーライドを実装します。  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## ヒット テストのサポート  
 ホスト コンテナー オブジェクトは、表示プロパティが表示されない場合でもイベント処理を提供できますが、その <xref:System.Windows.UIElement.Visibility%2A> プロパティは必ず <xref:System.Windows.Visibility> に設定する必要があります。  これにより、マウスの左ボタンが離されるなどのマウス イベントをトラップできる、ホスト コンテナーのイベント処理ルーチンを作成できます。  作成されたイベント処理ルーチンは、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> メソッドを呼び出してヒット テストを実装できます。  このメソッドの <xref:System.Windows.Media.HitTestResultCallback> パラメーターは、ヒット テストの結果アクションを決定するために使用できるユーザー定義のプロシージャを参照します。  
  
 次の例では、ホスト コンテナー オブジェクトとその子に対してヒット テストのサポートを実装します。  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## 参照  
 <xref:System.Windows.Media.DrawingVisual>   
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)