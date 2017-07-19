---
title: "方法 : IScrollInfo インターフェイスを使用してコンテンツをスクロールする | Microsoft Docs"
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
  - "IScrollInfo インターフェイス"
  - "スクロール (コンテンツを)"
  - "ScrollViewer コントロール, スクロール (コンテンツを)"
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : IScrollInfo インターフェイスを使用してコンテンツをスクロールする
この例では、<xref:System.Windows.Controls.Primitives.IScrollInfo> インターフェイスを使用して、コンテンツをスクロールする方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> インターフェイスの機能の例を次に示します。  この例では、親 <xref:System.Windows.Controls.ScrollViewer> に入れ子にされている <xref:System.Windows.Controls.StackPanel> 要素を [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で作成します。  <xref:System.Windows.Controls.StackPanel> の子要素を、<xref:System.Windows.Controls.Primitives.IScrollInfo> インターフェイスで定義されたメソッドを使って論理的にスクロールし、コード内で <xref:System.Windows.Controls.StackPanel> のインスタンス \(`sp1`\) にキャストすることができます。  
  
 [!code-xml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル内の各 <xref:System.Windows.Controls.Button> は、<xref:System.Windows.Controls.StackPanel> 内でのスクロール動作を制御する関連したカスタム メソッドをトリガーします。  次の例は、<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> メソッドおよび <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> メソッドの使用方法を示しています。また、<xref:System.Windows.Controls.Primitives.IScrollInfo> クラスで定義されているすべての配置メソッドの一般的な使用方法も示しています。  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## 参照  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.Primitives.IScrollInfo>   
 <xref:System.Windows.Controls.StackPanel>   
 [ScrollViewer の概要](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)