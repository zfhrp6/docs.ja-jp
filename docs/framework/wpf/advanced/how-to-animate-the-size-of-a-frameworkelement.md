---
title: "方法 : FrameworkElement のサイズをアニメーション化する | Microsoft Docs"
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
  - "アニメーション, FrameworkElement のサイズ"
  - "FrameworkElement, アニメーション化 (サイズを)"
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : FrameworkElement のサイズをアニメーション化する
<xref:System.Windows.FrameworkElement> のサイズをアニメーション化するには、その <xref:System.Windows.FrameworkElement.Width%2A> プロパティと <xref:System.Windows.FrameworkElement.Height%2A> プロパティをアニメーション化するか、アニメーション化された <xref:System.Windows.Media.ScaleTransform> を使用します。  
  
 次の例では、この 2 つの方法を使用して 2 つのボタンのサイズをアニメーション化します。  <xref:System.Windows.FrameworkElement.Width%2A> プロパティをアニメーション化することで一方のボタンのサイズを変更し、<xref:System.Windows.UIElement.RenderTransform%2A> プロパティに適用される <xref:System.Windows.Media.ScaleTransform> をアニメーション化することでもう一方のボタンのサイズを変更します。  各ボタンにはテキストが含まれています。  最初は、両方のボタンでテキストが同じように表示されますが、ボタンのサイズを変更すると、2 番目のボタンのテキストがゆがめられます。  
  
## 使用例  
 [!code-xml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 要素を変換すると、要素全体とそのコンテンツが変換されます。  最初のボタンのように、要素のサイズを直接変更した場合、要素のサイズと位置が親要素のサイズに依存していない限り、要素のコンテンツのサイズは変更されません。  
  
 アニメーション化された変換を <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに適用して要素のサイズをアニメーション化すると、その要素の <xref:System.Windows.FrameworkElement.Width%2A> と <xref:System.Windows.FrameworkElement.Height%2A> を直接アニメーション化するよりもパフォーマンスが向上します。これは、<xref:System.Windows.UIElement.RenderTransform%2A> プロパティがレイアウト パスをトリガーしないためです。  
  
 プロパティのアニメーション化の詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  トランザクションの詳細については、「[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)」を参照してください。