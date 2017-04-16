---
title: "方法 : ビジュアルのオフセットを取得する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "取得 (ビジュアル オブジェクトからオフセット値を)"
  - "オフセット値, 取得 (ビジュアル オブジェクトから)"
  - "取得 (ビジュアル オブジェクトからオフセット値を)"
  - "ビジュアル オブジェクト, 取得 (オフセット値を)"
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : ビジュアルのオフセットを取得する
この例では、親、先祖、または子孫を基準とした相対値である、ビジュアル オブジェクトのオフセット値を取得する方法を示します。  
  
## 使用例  
 次に示すマークアップの例では、<xref:System.Windows.Controls.TextBlock> の <xref:System.Windows.FrameworkElement.Margin%2A> の値に 4 が指定されています。  
  
 [!code-xml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> メソッドを使用して <xref:System.Windows.Controls.TextBlock> のオフセットを取得する方法を次の例に示します。  オフセット値は、返される <xref:System.Windows.Vector> 値に含まれます。  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 オフセットでは、<xref:System.Windows.FrameworkElement.Margin%2A> 値が考慮されます。  ここでは、<xref:System.Windows.Vector.X%2A> は 4 で、<xref:System.Windows.Vector.Y%2A> も 4 です。  
  
 返されるオフセット値は、<xref:System.Windows.Media.Visual> の親を基準とする相対値です。  <xref:System.Windows.Media.Visual> の親が基準ではないオフセット値を返す必要がある場合は、<xref:System.Windows.Media.Visual.TransformToAncestor%2A> メソッドを使用します。  
  
## 先祖を基準としたオフセットの取得  
 2 つの <xref:System.Windows.Controls.StackPanel> オブジェクトの中で入れ子になっている <xref:System.Windows.Controls.TextBlock> のマークアップ例を次に示します。  
  
 [!code-xml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 マークアップの結果を次の図に示します。  
  
 ![オブジェクトのオフセット値](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset\_01")  
2 つの StackPanel 内で入れ子にされた TextBlock  
  
 <xref:System.Windows.Media.Visual.TransformToAncestor%2A> メソッドを使用して、<xref:System.Windows.Controls.TextBlock> のオフセットを、このオブジェクトを格納している <xref:System.Windows.Window> を基準として取得する方法を次のコード例に示します。  オフセット値は、返される <xref:System.Windows.Media.GeneralTransform> 値に含まれます。  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 オフセットの値は、そのオブジェクトを格納している <xref:System.Windows.Window> 内のすべてのオブジェクトの <xref:System.Windows.FrameworkElement.Margin%2A> 値を考慮して計算されます。  この例では、<xref:System.Windows.Vector.X%2A> は 28 \(16 \+ 8 \+ 4\) で、<xref:System.Windows.Vector.Y%2A> も 28 です。  
  
 返されるオフセット値は、<xref:System.Windows.Media.Visual> の先祖を基準としています。  <xref:System.Windows.Media.Visual> の子孫を基準とするオフセット値を返す必要がある場合は、<xref:System.Windows.Media.Visual.TransformToDescendant%2A> メソッドを使用します。  
  
## 子孫を基準としたオフセットの取得  
 <xref:System.Windows.Controls.StackPanel> オブジェクトに格納されている <xref:System.Windows.Controls.TextBlock> のマークアップ例を次に示します。  
  
 [!code-xml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <xref:System.Windows.Media.Visual.TransformToDescendant%2A> メソッドを使用して、子 <xref:System.Windows.Controls.TextBlock> を基準にして <xref:System.Windows.Controls.StackPanel> のオフセットを取得する方法を次のコード例に示します。  オフセット値は、返される <xref:System.Windows.Media.GeneralTransform> 値に含まれます。  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 オフセットでは、すべてのオブジェクトの <xref:System.Windows.FrameworkElement.Margin%2A> 値が考慮されます。  ここでは、<xref:System.Windows.Vector.X%2A> は \-4 で、<xref:System.Windows.Vector.Y%2A> も \-4 です。  これらのオフセット値が負の値である理由は、子オブジェクトを基準とした親オブジェクトのオフセットが負のオフセットであるためです。  
  
## 参照  
 <xref:System.Windows.Media.Visual>   
 <xref:System.Windows.Media.VisualTreeHelper>   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)