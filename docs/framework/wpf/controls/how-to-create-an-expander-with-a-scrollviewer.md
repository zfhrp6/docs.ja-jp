---
title: "方法 : ScrollViewer を持つエキスパンダーを作成する | Microsoft Docs"
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
  - "コントロール [WPF], Expander"
  - "コントロール [WPF], ScrollViewer"
  - "Expander コントロール, 作成"
  - "ScrollViewer コントロール, Expander コントロールを備えた"
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : ScrollViewer を持つエキスパンダーを作成する
この例では、イメージやテキストなどの複雑なコンテンツを格納した <xref:System.Windows.Controls.Expander> コントロールを作成する方法を示します。  また、この例では、<xref:System.Windows.Controls.Expander> のコンテンツを <xref:System.Windows.Controls.ScrollViewer> コントロールで囲む方法も示します。  
  
## 使用例  
 <xref:System.Windows.Controls.Expander> の作成方法を次の例に示します。  この例では、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A> を定義するために、イメージとテキストを含む <xref:System.Windows.Controls.Primitives.BulletDecorator> コントロールを使用しています。  <xref:System.Windows.Controls.ScrollViewer> コントロールは、展開されたコンテンツをスクロールするメソッドを提供します。  
  
 この例では、コンテンツに対してではなく、<xref:System.Windows.Controls.ScrollViewer> に対して <xref:System.Windows.FrameworkElement.Height%2A> プロパティを設定していることに注意してください。  <xref:System.Windows.FrameworkElement.Height%2A> をコンテンツに対して設定すると、<xref:System.Windows.Controls.ScrollViewer> はコンテンツのスクロールを許可しなくなります。  <xref:System.Windows.FrameworkElement.Width%2A> プロパティは <xref:System.Windows.Controls.Expander> コントロールで設定され、この設定は、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A> および展開されたコンテンツに対して適用されます。  
  
 [!code-xml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## 参照  
 <xref:System.Windows.Controls.Expander>   
 [エキスパンダーの概要](../../../../docs/framework/wpf/controls/expander-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)