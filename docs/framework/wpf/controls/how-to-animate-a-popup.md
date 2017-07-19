---
title: "方法 : ポップアップをアニメーション化する | Microsoft Docs"
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
  - "アニメーション, ポップアップ コントロール"
  - "Popup コントロール, アニメーション化"
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ポップアップをアニメーション化する
ここでは、<xref:System.Windows.Controls.Primitives.Popup> コントロールをアニメーション化する 2 つの方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.Primitives.PopupAnimation> プロパティを <xref:System.Windows.Controls.Primitives.PopupAnimation> の値に設定して、<xref:System.Windows.Controls.Primitives.Popup> を "スライド イン" させながら表示する例を次に示します。  
  
 <xref:System.Windows.Controls.Primitives.Popup> を回転させるため、この例では <xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Controls.Canvas> \(<xref:System.Windows.Controls.Primitives.Popup> の子要素\) の <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに割り当てています。  
  
 この変換が正常に動作するためには、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> プロパティを `true` に設定する必要があります。  また、<xref:System.Windows.Controls.Canvas> コンテンツの <xref:System.Windows.FrameworkElement.Margin%2A> で、<xref:System.Windows.Controls.Primitives.Popup> が回転するのに十分な領域を指定する必要があります。  
  
 [!code-xml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <xref:System.Windows.Controls.Button> をクリックすると発生する <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントが、アニメーションを開始する <xref:System.Windows.Media.Animation.Storyboard> をトリガーする方法を次の例に示します。  
  
 [!code-xml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## 参照  
 <xref:System.Windows.UIElement.RenderTransform%2A>   
 <xref:System.Windows.Controls.Primitives.BulletDecorator>   
 <xref:System.Windows.Media.RotateTransform>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 <xref:System.Windows.Controls.Primitives.Popup>   
 [方法のトピック](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)   
 [ポップアップの概要](../../../../docs/framework/wpf/controls/popup-overview.md)