---
title: "パフォーマンスの最適化 : その他の推奨事項 | Microsoft Docs"
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
  - "ブラシ, パフォーマンス"
  - "ヒットテスト (オブジェクトの) [WPF]"
  - "不透明"
  - "ScrollBarVisibility 列挙体"
  - "ターミナル サービスのレンダリング"
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# パフォーマンスの最適化 : その他の推奨事項
<a name="introduction"></a> このトピックでは、「[WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)」のトピックで説明されている推奨事項を補足するパフォーマンスに関する推奨事項について説明します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [ブラシの Opacity と要素の Opacity](#Opacity)  
  
-   [オブジェクトへの移動](#Navigation_Objects)  
  
-   [大きな 3D サーフェイスのヒット テスト](#Hit_Testing)  
  
-   [CompositionTarget.Rendering イベント](#CompositionTarget_Rendering_Event)  
  
-   [ScrollBarVisibility\=Auto は使用しない](#Avoid_Using_ScrollBarVisibility)  
  
-   [Font Cache サービスの構成による起動時間の短縮](#FontCache)  
  
<a name="Opacity"></a>   
## ブラシの Opacity と要素の Opacity  
 <xref:System.Windows.Media.Brush> を使用して要素の <xref:System.Windows.Shapes.Shape.Fill%2A> や <xref:System.Windows.Shapes.Shape.Stroke%2A> を設定するときには、要素の <xref:System.Windows.UIElement.Opacity%2A> プロパティを設定するより <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=fullName> 値を設定することをお勧めします。  要素の <xref:System.Windows.UIElement.Opacity%2A> プロパティを変更すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって一時的なサーフェイスが作成される可能性があります。  
  
<a name="Navigation_Objects"></a>   
## オブジェクトへの移動  
 <xref:System.Windows.Navigation.NavigationWindow> オブジェクトは <xref:System.Windows.Window> から派生し、コンテンツ ナビゲーションのサポートでウィンドウを拡張します。この拡張は、主に <xref:System.Windows.Navigation.NavigationService> と履歴を統合することによって行われます。  <xref:System.Windows.Navigation.NavigationWindow> のクライアント領域は、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] またはオブジェクトを指定することによって更新できます。  この両方の方法を次のサンプルに示します。  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 各 <xref:System.Windows.Navigation.NavigationWindow> オブジェクトには、そのウィンドウのユーザーのナビゲーションを記録する履歴があります。  履歴の目的の 1 つは、ユーザーが自分の来た道を戻れるようにすることです。  
  
 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] を使用して移動した場合、履歴には [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] の参照のみが格納されます。  したがって、ページに戻るたびにそのページが動的に再構築されることになり、ページの複雑さによってはかなりの時間がかかることもあります。  この場合、履歴の格納の負荷は低い反面、ページの再構築にかかる時間が長くなる可能性があります。  
  
 オブジェクトを使用して移動した場合は、オブジェクトのビジュアル ツリー全体が履歴に格納されます。  したがって、ページに戻るたびにページを再構築する必要はなく、ページがすぐに描画されます。  この場合、履歴の格納の負荷は高くなりますが、ページの再構築にかかる時間は短くて済みます。  
  
 <xref:System.Windows.Navigation.NavigationWindow> オブジェクトを使用するときには、履歴のサポートがアプリケーションのパフォーマンスにどのように影響するのかを念頭に置いておく必要があります。  詳細については、「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。  
  
<a name="Hit_Testing"></a>   
## 大きな 3D サーフェイスのヒット テスト  
 大きな 3D サーフェイスのヒット テストは、CPU 消費の面でパフォーマンスへの影響が非常に大きくなります。  3D サーフェイスがアニメーション化されている場合には特にその傾向が強くなります。  そのようなサーフェイスでヒット テストを行う必要がない場合は、ヒット テストを無効にしてください。  <xref:System.Windows.UIElement> から派生したオブジェクトでは、<xref:System.Windows.UIElement.IsHitTestVisible%2A> プロパティを `false` に設定することによってヒット テストを無効にできます。  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## CompositionTarget.Rendering イベント  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=fullName> イベントは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を常にアニメーション化します。  このイベントを使用する場合は、毎回デタッチしてください。  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## ScrollBarVisibility\=Auto は使用しない  
 できる限り、<xref:System.Windows.Controls.ScrollBarVisibility?displayProperty=fullName> 値を `HorizontalScrollBarVisibility` プロパティと `VerticalScrollBarVisibility` プロパティでは使用しないでください。  これらのプロパティは、<xref:System.Windows.Controls.RichTextBox>、<xref:System.Windows.Controls.ScrollViewer>、<xref:System.Windows.Controls.TextBox>、<xref:System.Windows.Controls.ListBox> の各オブジェクトで定義されています。  代わりに、<xref:System.Windows.Controls.ScrollBarVisibility> を <xref:System.Windows.Controls.ScrollBarVisibility>、<xref:System.Windows.Controls.ScrollBarVisibility>、または <xref:System.Windows.Controls.ScrollBarVisibility> に設定します。  
  
 <xref:System.Windows.Controls.ScrollBarVisibility> 値は、スペースが限られていて、スクロール バーを必要なときにだけ表示する場合に使用するための値です。  <xref:System.Windows.Controls.ScrollBarVisibility> 値の使用は、たとえば、数百行のテキストを含む <xref:System.Windows.Controls.TextBox> ではなく、30 の項目を含む <xref:System.Windows.Controls.ListBox> で役に立ちます。  
  
<a name="FontCache"></a>   
## Font Cache サービスの構成による起動時間の短縮  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Font Cache サービスは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーション間でフォント データを共有します。  このサービスがまだ実行されていない場合は、実行する最初の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションによって開始されます。  [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] を使用している場合は、\[[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Font Cache 3.0.0.0\] サービスの設定を \[手動\] \(既定\) から \[自動 \(遅延開始\)\] に変更することで、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの最初の起動時間を短縮できます。  
  
## 参照  
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [テキスト](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [アニメーションのヒントとテクニック](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)