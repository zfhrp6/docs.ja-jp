---
title: "方法 : 要素の Height プロパティを設定する"
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
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ae66e60375cfbc45a4f1e8834b6420bc5c0b70a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>方法 : 要素の Height プロパティを設定する
## <a name="example"></a>例  
 この例は、レンダリングの 4 つの高さに関連したプロパティの間での動作の違いを視覚的にでは[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。  
  
 <xref:System.Windows.FrameworkElement>クラスは、要素の高さの特性を説明する 4 つのプロパティを公開します。 これら 4 つのプロパティが競合することと優先する値は次のように決定されます、:<xref:System.Windows.FrameworkElement.MinHeight%2A>値よりも優先、<xref:System.Windows.FrameworkElement.MaxHeight%2A>値で、さらによりも優先、<xref:System.Windows.FrameworkElement.Height%2A>値。 4 番目のプロパティ<xref:System.Windows.FrameworkElement.ActualHeight%2A>は読み取り専用、およびレイアウトの処理との対話によって決定される実際の高さを報告します。  
  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例の描画、<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) の子として<xref:System.Windows.Controls.Canvas>です。 高さのプロパティを変更することができます、<xref:System.Windows.Shapes.Rectangle>の系列を使用して、<xref:System.Windows.Controls.ListBox>のプロパティ値を表す要素<xref:System.Windows.FrameworkElement.MinHeight%2A>、 <xref:System.Windows.FrameworkElement.MaxHeight%2A>、および<xref:System.Windows.FrameworkElement.Height%2A>です。 この方法で各プロパティの優先度が視覚的に表示されます。  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 次のコード ビハインド例は、イベントを処理する、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>イベントを発生させます。 各ハンドラーからの入力を受け取り、 <xref:System.Windows.Controls.ListBox>、として値を解析して、 <xref:System.Double>、し、指定した高さに関連するプロパティに値を適用します。 高さの値も文字列に変換され、さまざまなに書き込まれる<xref:System.Windows.Controls.TextBlock>要素 (それらの要素の定義は、選択した XAML には表示されません)。  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 サンプル全体については、次を参照してください。[高さのプロパティのサンプル](http://go.microsoft.com/fwlink/?LinkID=159993)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [要素の Width プロパティを設定する](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [高さのプロパティのサンプル](http://go.microsoft.com/fwlink/?LinkID=159993)
