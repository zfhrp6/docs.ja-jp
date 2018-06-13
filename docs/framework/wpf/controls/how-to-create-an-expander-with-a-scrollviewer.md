---
title: '方法 : ScrollViewer を持つエキスパンダーを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 6c014d4f6a12bfb58c2ae68f580f632c9478c82f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553063"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>方法 : ScrollViewer を持つエキスパンダーを作成する
この例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>イメージやテキストなどの複雑なコンテンツを格納するコントロール。 この例ものコンテンツを囲む、<xref:System.Windows.Controls.Expander>で、<xref:System.Windows.Controls.ScrollViewer>コントロール。  
  
## <a name="example"></a>例  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>です。 この例では、<xref:System.Windows.Controls.Primitives.BulletDecorator>を定義するのには画像とテキストを含むコントロール、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>です。 A<xref:System.Windows.Controls.ScrollViewer>コントロールに展開されたコンテンツをスクロールするためのメソッドが用意されています。  
  
 例では、セット、<xref:System.Windows.FrameworkElement.Height%2A>プロパティを<xref:System.Windows.Controls.ScrollViewer>の代わりに、コンテンツにします。 場合、 <xref:System.Windows.FrameworkElement.Height%2A> 、コンテンツに設定されている、<xref:System.Windows.Controls.ScrollViewer>ユーザー コンテンツをスクロールすることはできません。 <xref:System.Windows.FrameworkElement.Width%2A>プロパティが設定されて、<xref:System.Windows.Controls.Expander>に制御し、この設定が適用されます、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>と展開されたコンテンツ。  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Expander>  
 [エキスパンダーの概要](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
