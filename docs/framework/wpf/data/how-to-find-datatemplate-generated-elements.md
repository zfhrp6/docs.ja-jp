---
title: "方法 : DataTemplate によって生成された要素を検索する | Microsoft Docs"
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
  - "DataTemplate"
  - "検索 (DataTemplate 要素を)"
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : DataTemplate によって生成された要素を検索する
この例では、<xref:System.Windows.DataTemplate> によって生成された要素の検索方法について説明します。  
  
## 使用例  
 この例には、ある [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データにバインドされた <xref:System.Windows.Controls.ListBox> が存在します。  
  
 [!code-xml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 この <xref:System.Windows.Controls.ListBox> は、次の <xref:System.Windows.DataTemplate> を使用します。  
  
 [!code-xml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 ある <xref:System.Windows.Controls.ListBoxItem> の <xref:System.Windows.DataTemplate> によって生成された <xref:System.Windows.Controls.TextBlock> 要素を取得するには、<xref:System.Windows.Controls.ListBoxItem> を取得し、その <xref:System.Windows.Controls.ListBoxItem> 内で <xref:System.Windows.Controls.ContentPresenter> を検索し、その <xref:System.Windows.Controls.ContentPresenter> に設定されている <xref:System.Windows.DataTemplate> に対して <xref:System.Windows.FrameworkTemplate.FindName%2A> を呼び出す必要があります。  次の例は、この手順の実行方法を示しています。  わかりやすくするため、この例では <xref:System.Windows.DataTemplate> で生成されたテキスト ブロックのテキスト コンテンツを表示するメッセージ ボックスを作成しています。  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 次に示すのは、`FindVisualChild` の実装です。この実装は、<xref:System.Windows.Media.VisualTreeHelper> メソッドを使用しています。  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## 参照  
 [方法 : ControlTemplate によって生成された要素を検索する](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [WPF XAML 名前スコープ](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)   
 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)