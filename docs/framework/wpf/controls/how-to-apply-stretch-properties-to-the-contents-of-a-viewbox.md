---
title: "方法 : Viewbox のコンテンツに Stretch プロパティを適用する | Microsoft Docs"
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
  - "コントロール, Viewbox"
  - "Stretch プロパティ"
  - "StretchDirection プロパティ"
  - "Viewbox コントロール"
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Viewbox のコンテンツに Stretch プロパティを適用する
## 使用例  
 この例では、<xref:System.Windows.Controls.Viewbox> の <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> プロパティの値と <xref:System.Windows.Controls.Viewbox.Stretch%2A> プロパティの値を変更する方法を示します。  
  
 最初の例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して <xref:System.Windows.Controls.Viewbox> 要素を定義します。  ここでは、400 の <xref:System.Windows.FrameworkElement.MaxWidth%2A> と 400 の <xref:System.Windows.FrameworkElement.MaxHeight%2A> を割り当てます。  この例では、<xref:System.Windows.Controls.Image> 要素を <xref:System.Windows.Controls.Viewbox> 内に入れ子にします。  <xref:System.Windows.Controls.Viewbox.Stretch%2A> 列挙体と <xref:System.Windows.Controls.StretchDirection> 列挙体のプロパティ値に対応する <xref:System.Windows.Controls.Button> 要素は、入れ子になった <xref:System.Windows.Controls.Image> の伸縮動作を操作します。  
  
 [!code-xml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 次の分離コード ファイルは、前の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例で定義した <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを処理します。  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## 参照  
 <xref:System.Windows.Controls.Viewbox>   
 <xref:System.Windows.Media.Stretch>   
 <xref:System.Windows.Controls.StretchDirection>