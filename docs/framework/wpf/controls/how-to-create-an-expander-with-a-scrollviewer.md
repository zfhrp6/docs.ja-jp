---
title: "方法 : ScrollViewer を持つエキスパンダーを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2066ccce28138cfecf4e0b4574d45783a9ba4ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>方法 : ScrollViewer を持つエキスパンダーを作成する
この例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>イメージやテキストなどの複雑なコンテンツを格納するコントロール。 この例ものコンテンツを囲む、<xref:System.Windows.Controls.Expander>で、<xref:System.Windows.Controls.ScrollViewer>コントロール。  
  
## <a name="example"></a>例  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>です。 この例では、<xref:System.Windows.Controls.Primitives.BulletDecorator>を定義するのには画像とテキストを含むコントロール、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>です。 A<xref:System.Windows.Controls.ScrollViewer>コントロールに展開されたコンテンツをスクロールするためのメソッドが用意されています。  
  
 例では、セット、<xref:System.Windows.FrameworkElement.Height%2A>プロパティを<xref:System.Windows.Controls.ScrollViewer>の代わりに、コンテンツにします。 場合、 <xref:System.Windows.FrameworkElement.Height%2A> 、コンテンツに設定されている、<xref:System.Windows.Controls.ScrollViewer>ユーザー コンテンツをスクロールすることはできません。 <xref:System.Windows.FrameworkElement.Width%2A>プロパティが設定されて、<xref:System.Windows.Controls.Expander>に制御し、この設定が適用されます、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>と展開されたコンテンツ。  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.Expander>  
 [エキスパンダーの概要](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
