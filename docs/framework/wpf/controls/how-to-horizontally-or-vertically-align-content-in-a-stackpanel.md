---
title: "方法 : StackPanel にコンテンツを水平方向または垂直方向に配置する | Microsoft Docs"
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
  - "エイリアスの使用, コンテンツ"
  - "コンテンツの配置"
  - "StackPanel コントロール, コンテンツの配置"
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : StackPanel にコンテンツを水平方向または垂直方向に配置する
この例では、<xref:System.Windows.Controls.StackPanel> 要素内のコンテンツの <xref:System.Windows.Controls.StackPanel.Orientation%2A> を調整する方法、および子コンテンツの <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> と <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> を調整する方法を示します。  
  
## 使用例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で 3 つの <xref:System.Windows.Controls.ListBox> 要素を作成する例を次に示します。  それぞれの <xref:System.Windows.Controls.ListBox> が、<xref:System.Windows.Controls.StackPanel> の <xref:System.Windows.Controls.StackPanel.Orientation%2A>、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、および <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> の各プロパティに指定できる値を表します。  ユーザーがいずれかの <xref:System.Windows.Controls.ListBox> 要素で値を選択すると、<xref:System.Windows.Controls.StackPanel> 要素の関連するプロパティと、その子要素である <xref:System.Windows.Controls.Button> が変わります。  
  
 [!code-xml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 次の分離コード ファイルでは、<xref:System.Windows.Controls.ListBox> の選択の変更に関連付けられているイベントに対する変更を定義します。  <xref:System.Windows.Controls.StackPanel> は、<xref:System.Windows.FrameworkElement.Name%2A> `sp1` で識別されます。  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## 参照  
 <xref:System.Windows.Controls.StackPanel>   
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)