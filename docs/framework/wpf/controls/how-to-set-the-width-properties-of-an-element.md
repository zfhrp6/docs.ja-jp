---
title: "方法 : 要素の Width プロパティを設定する"
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
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 830289f13ac89601f0d3539e2f4400e56a2476f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>方法 : 要素の Width プロパティを設定する
## <a name="example"></a>例  
 この例は、レンダリングの 4 つの幅に関連するプロパティの間での動作の違いを視覚的にでは[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。  
  
 <xref:System.Windows.FrameworkElement>クラスは、要素の幅の特性を説明する 4 つのプロパティを公開します。 これら 4 つのプロパティが競合することと優先する値は次のように決定されます、:<xref:System.Windows.FrameworkElement.MinWidth%2A>値よりも優先、<xref:System.Windows.FrameworkElement.MaxWidth%2A>値で、さらによりも優先、<xref:System.Windows.FrameworkElement.Width%2A>値。 4 番目のプロパティ<xref:System.Windows.FrameworkElement.ActualWidth%2A>は読み取り専用、およびレイアウトの処理との対話によって決定される実際の幅を報告します。  
  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例の描画、<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) の子として<xref:System.Windows.Controls.Canvas>です。 幅のプロパティを変更することができます、<xref:System.Windows.Shapes.Rectangle>の系列を使用して、<xref:System.Windows.Controls.ListBox>のプロパティ値を表す要素<xref:System.Windows.FrameworkElement.MinWidth%2A>、 <xref:System.Windows.FrameworkElement.MaxWidth%2A>、および<xref:System.Windows.FrameworkElement.Width%2A>です。 この方法で各プロパティの優先度が視覚的に表示されます。  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 次のコード ビハインド例は、イベントを処理する、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>イベントを発生させます。 各カスタム メソッドからの入力を受け取り、 <xref:System.Windows.Controls.ListBox>、として値を解析して、 <xref:System.Double>、し、指定した幅に関連するプロパティに値を適用します。 幅の値も文字列に変換され、さまざまなに書き込まれる<xref:System.Windows.Controls.TextBlock>要素 (それらの要素の定義は、選択した XAML には表示されません)。  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 サンプル全体については、次を参照してください。[幅のプロパティの比較サンプル](http://go.microsoft.com/fwlink/?LinkID=160050)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [要素の Height プロパティを設定する](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [幅のプロパティの比較サンプル](http://go.microsoft.com/fwlink/?LinkID=160050)
