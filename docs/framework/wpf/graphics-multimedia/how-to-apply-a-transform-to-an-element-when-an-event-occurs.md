---
title: "方法 : イベントの発生時に要素に変換を適用する | Microsoft Docs"
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
  - "グラフィックス, 変換 (イベント応答として)"
  - "LayoutTransform プロパティ"
  - "プロパティ, LayoutTransform"
  - "プロパティ, RenderTransform"
  - "RenderTransform プロパティ"
  - "変換 (イベント応答として)"
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : イベントの発生時に要素に変換を適用する
この例では、イベントの発生時に <xref:System.Windows.Media.ScaleTransform> を適用する方法を示します。  ここで示される概念は、他の種類の変換を適用する場合に使用するものと同じです。  使用可能な変換の種類の詳細については、<xref:System.Windows.Media.Transform> クラスまたは「[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)」を参照してください。  
  
 要素に変換を適用するには、次の 2 つの方法があります。  
  
-   変換がレイアウトに影響しないようにする場合は、要素の <xref:System.Windows.UIElement.RenderTransform%2A> プロパティを使用します。  
  
-   変換がレイアウトに影響するようにする場合は、要素の <xref:System.Windows.FrameworkElement.LayoutTransform%2A> プロパティを使用します。  
  
 次の例では、ボタンの <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに <xref:System.Windows.Media.ScaleTransform> を適用しています。  マウスをボタンの上に移動すると、<xref:System.Windows.Media.ScaleTransform> の <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> プロパティと <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> プロパティが `2` に設定され、ボタンが大きくなります。  マウスがボタンから離れると、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A> と <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> が `1` に設定され、ボタンは元のサイズに戻ります。  
  
## 使用例  
 [!code-xml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## 参照  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.ScaleTransform>   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)