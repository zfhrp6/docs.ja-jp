---
title: "パフォーマンスの最適化 : アプリケーション リソース | Microsoft Docs"
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
  - "アプリケーション リソース, パフォーマンス"
  - "ブラシ, パフォーマンス"
  - "リソース, パフォーマンス"
  - "共有 (コピーせずにブラシを)"
  - "共有 (リソースを)"
  - "静的リソース"
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# パフォーマンスの最適化 : アプリケーション リソース
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、アプリケーション リソースを共有して、同じような種類の要素の間で外観や動作の一貫性を維持することができます。  このトピックでは、アプリケーションのパフォーマンス向上に役立つリソース関連の推奨事項について説明します。  
  
 リソースの詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
## リソースの共有  
 アプリケーションでカスタム コントロールを使用していて、<xref:System.Windows.ResourceDictionary> \(または XAML Resources ノード\) でリソースを定義している場合は、<xref:System.Windows.Application> オブジェクトまたは <xref:System.Windows.Window> オブジェクトのレベルで定義するか、カスタム コントロールの既定のテーマで定義することをお勧めします。  カスタム コントロールの <xref:System.Windows.ResourceDictionary> でリソースを定義すると、そのコントロールのすべてのインスタンスにパフォーマンスの影響が及びます。  たとえば、負荷の高いブラシ操作がカスタム コントロールとその多くのインスタンスのリソース定義の一部として定義されていると、アプリケーションの作業セットが大幅に増大します。  
  
 これを実際の例で考えてみましょう。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を使用してトランプ ゲームを開発するとします。  ほとんどのトランプ ゲームでは、それぞれ異なる面を持つ 52 枚のカードが必要です。  そのためにカード カスタム コントロールを実装することにして、そのリソースで 52 のブラシを定義します \(各ブラシはそれぞれカードの面を表します\)。  メイン アプリケーションでは、最初にこのカード カスタム コントロールの 52 のインスタンスを作成します。  カード カスタム コントロールの各インスタンスでは、それぞれ <xref:System.Windows.Media.Brush> オブジェクトの 52 のインスタンスが生成されます。その結果、全部で 52 × 52 の <xref:System.Windows.Media.Brush> オブジェクトがアプリケーションに存在することになります。  ブラシをカード カスタム コントロールのリソースから <xref:System.Windows.Application> オブジェクトまたは <xref:System.Windows.Window> オブジェクトのレベルに移動するか、カスタム コントロールの既定のテーマで定義すると、カード コントロールの 52 のインスタンスの間で 52 のブラシが共有されるようになるため、アプリケーションの作業セットが縮小されます。  
  
## ブラシはコピーせずに共有する  
 同じ <xref:System.Windows.Media.Brush> オブジェクトを使用する複数の要素がある場合は、ブラシを [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] でインラインで定義するのではなく、リソースとして定義して参照するようにします。  この方法を使用すると、1 つのインスタンスを作成してそれを再利用することができます。一方、ブラシを [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] でインラインで定義した場合は、各要素に対して新しいインスタンスが作成されます。  
  
 この例を次のマークアップ サンプルに示します。  
  
 [!code-xml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## 可能な限り静的リソースを使用する  
 静的リソースは、既に定義されたリソースに対する参照を検索することによって、任意の XAML プロパティ属性の値を指定します。  そのリソースに関する検索動作は、コンパイル時の検索に似ています。  
  
 一方、動的リソースは、初期コンパイル中に一時的な式を作成し、それによって、要求されたリソース値がオブジェクトを構成するために実際に必要になるまで、リソースに関する検索を遅延します。  そのリソースに関する検索動作は、実行時検索に似ています。これはパフォーマンスに影響します。  アプリケーションでは可能な限り静的リソースを使用し、動的リソースを使用するのは必要な場合だけにしてください。  
  
 次のマークアップ サンプルでは、この両方の種類のリソースが使用されています。  
  
 [!code-xml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## 参照  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [テキスト](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)