---
title: "方法 : DataTemplate によって生成された要素を検索する"
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
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22d5f393d376935f04459e2713e9658c80af6efa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-datatemplate-generated-elements"></a>方法 : DataTemplate によって生成された要素を検索する
この例によって生成される要素を検索する方法を示しています、<xref:System.Windows.DataTemplate>です。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Windows.Controls.ListBox>一部にバインドされた[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データ。  
  
 [!code-xaml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> 、次を使用して<xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 取得する場合、<xref:System.Windows.Controls.TextBlock>要素によって生成された、<xref:System.Windows.DataTemplate>特定の<xref:System.Windows.Controls.ListBoxItem>、取得する必要があります、 <xref:System.Windows.Controls.ListBoxItem>、検索、<xref:System.Windows.Controls.ContentPresenter>内<xref:System.Windows.Controls.ListBoxItem>、およびを呼び出す<xref:System.Windows.FrameworkTemplate.FindName%2A>上、 <xref:System.Windows.DataTemplate>設定されている<xref:System.Windows.Controls.ContentPresenter>です。 次の例では、これらの手順を実行する方法を示します。 デモのために、この例で作成、テキストを示すメッセージ ボックスのコンテンツ、 <xref:System.Windows.DataTemplate>-テキスト ブロックを生成します。  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 実装を次に示します`FindVisualChild`が使用される、<xref:System.Windows.Media.VisualTreeHelper>メソッド。  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>関連項目  
 [方法: ControlTemplate によって生成された要素を検索する](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [WPF XAML 名前スコープ](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
