---
title: "方法: ScrollChanged イベントを処理する | Microsoft Docs"
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
  - "ScrollChanged イベント"
  - "ScrollViewer コントロール, 発生 (ScrollChanged イベントを)"
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法: ScrollChanged イベントを処理する
## 使用例  
 この例では、<xref:System.Windows.Controls.ScrollViewer> の <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> イベントを処理する方法を示します。  
  
 <xref:System.Windows.Documents.Paragraph> パーツを含む <xref:System.Windows.Documents.FlowDocument> 要素が、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で定義されています。  ユーザーの操作によって <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> イベントが発生すると、ハンドラーが呼び出されて、イベントが発生したことを示すテキストが <xref:System.Windows.Controls.TextBlock> に書き込まれます。  
  
 [!code-xml[scrollchangedeventargsLayout#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xml[scrollchangedeventargsLayout#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## 参照  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>   
 <xref:System.Windows.Controls.ScrollChangedEventHandler>   
 <xref:System.Windows.Controls.ScrollChangedEventArgs>