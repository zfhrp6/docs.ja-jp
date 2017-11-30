---
title: "ScrollViewer の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6398e4a40a1d4a83bc0ae080321112fb6d9fcd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="scrollviewer-overview"></a>ScrollViewer の概要
ユーザー インターフェイス内のコンテンツは、多くの場合、コンピューター画面の表示領域よりも大きいです。 <xref:System.Windows.Controls.ScrollViewer>コントロール内のコンテンツのスクロールを有効にする便利な手段を提供する[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションです。 このトピックでは、<xref:System.Windows.Controls.ScrollViewer>要素し、いくつかの使用例を提供します。  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>ScrollViewer コントロール  
 スクロールを有効にする 2 つの定義済み要素がある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション:<xref:System.Windows.Controls.Primitives.ScrollBar>と<xref:System.Windows.Controls.ScrollViewer>です。 <xref:System.Windows.Controls.ScrollViewer>水平および垂直コントロールをカプセル化<xref:System.Windows.Controls.Primitives.ScrollBar>要素およびコンテンツのコンテナー (など、<xref:System.Windows.Controls.Panel>要素)、スクロール可能な領域に表示されるその他の要素を表示するためにします。 使用するためにカスタム オブジェクトを構築する必要があります、<xref:System.Windows.Controls.Primitives.ScrollBar>コンテンツのスクロールのための要素。 ただし、使用することができます、<xref:System.Windows.Controls.ScrollViewer>要素自体では、複合を制御するためをカプセル化<xref:System.Windows.Controls.Primitives.ScrollBar>機能します。  
  
 <xref:System.Windows.Controls.ScrollViewer>コントロールはマウスとキーボードの両方のコマンドに応答し、コンテンツを事前に定義されたずつスクロールに使用するさまざまなメソッドを定義します。 使用することができます、<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>で変更を検出するイベント、<xref:System.Windows.Controls.ScrollViewer>状態です。  
  
 A<xref:System.Windows.Controls.ScrollViewer>しか持てない 1 つの子では、通常、<xref:System.Windows.Controls.Panel>要素をホストできる、<xref:System.Windows.Controls.Panel.Children%2A>要素のコレクション。 <xref:System.Windows.Controls.ContentPresenter.Content%2A>プロパティ定義の唯一の子、<xref:System.Windows.Controls.ScrollViewer>です。  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>物理スクロールと論理スクロール  
 物理スクロールは、定義済みの物理インクリメント(通常ピクセル単位で宣言されている値) でコンテンツをスクロールするために使用します。 論理スクロールは、論理ツリーの次の項目にスクロールするために使用します。 ほとんどの既定のスクロール動作は、物理スクロール<xref:System.Windows.Controls.Panel>要素。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は両方の種類のスクロールをサポートしています。  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo インターフェイス  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイスを表しますメインのスクロール領域内で、<xref:System.Windows.Controls.ScrollViewer>またはコントロールを派生します。 スクロールのプロパティとメソッドを実装することができるインターフェイスが定義<xref:System.Windows.Controls.Panel>スクロール物理インクリメントではなく、論理ユニットを必要とします。 インスタンスのキャスト<xref:System.Windows.Controls.Primitives.IScrollInfo>派生に<xref:System.Windows.Controls.Panel>をピクセル単位ではなく、子のコレクションでは、次の論理ユニットにスクロールする便利な方法を提供し、そのスクロール メソッドを使用するとします。 既定では、<xref:System.Windows.Controls.ScrollViewer>コントロールは物理的な単位でスクロールをサポートします。  
  
 <xref:System.Windows.Controls.StackPanel>および<xref:System.Windows.Controls.VirtualizingStackPanel>両方を実装<xref:System.Windows.Controls.Primitives.IScrollInfo>とネイティブ論理スクロールをサポートします。 レイアウトがスクロールするにはネイティブ サポート論理をコントロールすることで実現ホストをラップすることによって物理スクロール<xref:System.Windows.Controls.Panel>内の要素、<xref:System.Windows.Controls.ScrollViewer>と設定、<xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>プロパティを`false`です。  
  
 インスタンスにキャストする方法を次のコード例に示します<xref:System.Windows.Controls.Primitives.IScrollInfo>を<xref:System.Windows.Controls.StackPanel>コンテンツのスクロール メソッドを使用して (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>と<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>)、インターフェイスによって定義されます。  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>ScrollViewer 要素の定義と使用  
 次の例を作成、<xref:System.Windows.Controls.ScrollViewer>いくつかのテキストと四角形を含むウィンドウ。 <xref:System.Windows.Controls.Primitives.ScrollBar>必要な要素が表示されます。 ウィンドウのサイズを変更するときに、<xref:System.Windows.Controls.Primitives.ScrollBar>要素が表示され、非表示の更新された値により、<xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A>と<xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>プロパティです。  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>ScrollViewer のスタイル設定  
 Windows Presentation Foundation では、すべてのコントロールと同様に、<xref:System.Windows.Controls.ScrollViewer>コントロールの既定のレンダリング動作を変更するためにスタイルを設定できます。 コントロールのスタイル設定の詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>ドキュメントの改ページ調整  
 ドキュメントのコンテンツでは、スクロールする代わりに、改ページ調整をサポートするドキュメントのコンテナーを選択します。 <xref:System.Windows.Documents.FlowDocument>など、表示するコントロール内でホストされるように設計されているドキュメントは<xref:System.Windows.Controls.FlowDocumentPageViewer>、不要にスクロールするため、複数のページ コンテンツの改ページ調整をサポートします。 <xref:System.Windows.Controls.DocumentViewer>表示するため、ソリューションを提供<xref:System.Windows.Documents.FixedDocument>コンテンツで、従来のスクロールを使用して、表示領域の領域外のコンテンツを表示します。  
  
 ドキュメント形式とプレゼンテーション オプションの詳細については、「[WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [スクロール ビューアーを作成します。](http://msdn.microsoft.com/en-us/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [ScrollBar のスタイルとテンプレート](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [コントロール](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
