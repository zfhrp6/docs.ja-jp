---
title: "方法 : ScrollViewer のコンテンツ スクロール メソッドを使用する | Microsoft Docs"
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
  - "スクロール メソッド"
  - "ScrollViewer コントロール, スクロール メソッド"
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ScrollViewer のコンテンツ スクロール メソッドを使用する
この例では、<xref:System.Windows.Controls.ScrollViewer> 要素のスクロール メソッドを使用する方法を示します。  これらのメソッドを使用すると、<xref:System.Windows.Controls.ScrollViewer> に表示されたコンテンツを行単位またはページ単位のインクリメント方式でスクロールできます。  
  
## 使用例  
 次の例では、<xref:System.Windows.Controls.TextBlock> 子要素をホストする `sv1` という名前の <xref:System.Windows.Controls.ScrollViewer> を作成します。  <xref:System.Windows.Controls.TextBlock> は親である <xref:System.Windows.Controls.ScrollViewer> を超えているため、スクロール バーが表示され、スクロールできるようになっています。  また、さまざまなスクロール メソッドを表す <xref:System.Windows.Controls.Button> 要素が、別の <xref:System.Windows.Controls.StackPanel> の左側にドッキングされます。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル内の各 <xref:System.Windows.Controls.Button> は、<xref:System.Windows.Controls.ScrollViewer> でのスクロール動作を制御する関連カスタム メソッドを呼び出します。  
  
 [!code-xml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 次の例では、<xref:System.Windows.Controls.ScrollViewer.LineUp%2A> メソッドと <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> メソッドを使用しています。  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## 参照  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.StackPanel>