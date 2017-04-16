---
title: "方法 : 要素のスピンを設定する | Microsoft Docs"
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
  - "クラス, DoubleAnimation"
  - "クラス, RotateTransform"
  - "DoubleAnimation クラス"
  - "グラフィックス, 回転 (要素を)"
  - "RotateTransform クラス"
  - "回転 (要素を)"
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 要素のスピンを設定する
この例では、<xref:System.Windows.Media.RotateTransform> と <xref:System.Windows.Media.Animation.DoubleAnimation> を使用して要素を回転させる方法を示します。  
  
 次の例では、要素の <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに <xref:System.Windows.Media.RotateTransform> を適用しています。  この例は、<xref:System.Windows.Media.Animation.DoubleAnimation> を使用して <xref:System.Windows.Media.RotateTransform> の <xref:System.Windows.Media.RotateTransform.Angle%2A> をアニメーション化します。  要素をその場で回転させるために、要素の <xref:System.Windows.UIElement.RenderTransformOrigin%2A> プロパティを点 \(0.5, 0.5\) に設定しています。  
  
## 使用例  
 [!code-xml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 さらに多くの変換の例が含まれるサンプル全体については、[2\-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)を参照してください。  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)