---
title: 'パフォーマンスの最適化 : アプリケーション リソース'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 53e906f31f32fb0f1df3f8d986daa0ae95ea9e4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546596"
---
# <a name="optimizing-performance-application-resources"></a>パフォーマンスの最適化 : アプリケーション リソース
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 同様に型指定された要素の間で一貫した外観や動作をサポートできるように、アプリケーションのリソースを共有できます。 このトピックでは、アプリケーションのパフォーマンスが向上するのに役立つこの領域で、いくつかの推奨事項を説明します。  
  
 リソースについて詳しくは、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」をご覧ください。  
  
## <a name="sharing-resources"></a>リソースの共有  
 アプリケーションがカスタム コントロールを使用して、内のリソースを定義するかどうか、 <xref:System.Windows.ResourceDictionary> (または XAML リソース ノード)、いずれかを定義することで、リソースをお勧め、<xref:System.Windows.Application>または<xref:System.Windows.Window>オブジェクト レベル、またはの既定のテーマで定義しますカスタム コントロールです。 カスタム コントロールのリソースを定義する<xref:System.Windows.ResourceDictionary>では、そのコントロールのすべてのインスタンス、パフォーマンスに影響します。 たとえば、カスタム コントロールのリソース定義の一部と、カスタム コントロールの多くのインスタンスとして定義されている負荷の高いブラシ操作がある場合は、アプリケーションのワーキング セットが大幅に増加されます。  
  
 このポイントを示すためには、次のことを検討してください。 たとえば、カード ゲームを使用して、開発している[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 ほとんどのカード ゲーム、それぞれ異なる面と 52 カードが必要です。 カードのカスタム コントロールを実装することし、カードのカスタム コントロールのリソースで (各を表すカードの面) 52 ブラシを定義します。 メイン アプリケーションでは、最初にこのカードのカスタム コントロールの 52 インスタンスを作成する必要があります。 カードのカスタム コントロールの各インスタンスの 52 のインスタンスが生成されます<xref:System.Windows.Media.Brush>オブジェクトで、により、合計で 52 * 52<xref:System.Windows.Media.Brush>アプリケーション内のオブジェクト。 リソースが不足、カード カスタム コントロールにブラシを移動することによって、<xref:System.Windows.Application>または<xref:System.Windows.Window>オブジェクト レベル、または、カスタム コントロールの既定のテーマでの定義 52 ブラシを共有しているようになりましたので、アプリケーションのワーキング セットを縮小します。カード コントロールの 52 のインスタンス。  
  
## <a name="sharing-a-brush-without-copying"></a>コピーすることがなく、ブラシの共有  
 同じを使用して複数の要素があれば<xref:System.Windows.Media.Brush>オブジェクト、リソースとしてブラシを定義しではなく、ブラシでインラインでの定義を参照[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]です。 このメソッドは 1 つのインスタンスが作成され、再利用できるよう、ブラシにインラインで定義する一方[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]の各要素の新しいインスタンスを作成します。  
  
 次のマークアップの例は、この点を示しています。  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>可能な場合は、静的なリソースを使用します。  
 静的リソースでは、定義済みのリソースへの参照を参照して、任意の XAML プロパティ属性の値を提供します。 そのリソースに対する検索の動作は、コンパイル時の検索に似ています。  
  
 動的リソースは、その一方で、最初のコンパイル中に一時的な式を作成、検索を遅延リソースに対して要求されたリソースの値が実際にオブジェクトを構築するために必要になるまでです。 そのリソースに対する検索の動作は、パフォーマンスに影響は、実行時の検索に似ています。 必要な場合にのみ、動的なリソースを使用して、アプリケーションで可能な限り、静的なリソースを使用します。  
  
 次のマークアップの例は、両方の種類のリソースの使用を示しています。  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [[テキスト]](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
