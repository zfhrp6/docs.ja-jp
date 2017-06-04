---
title: "方法 : UIElement を左右または上下に反転させる | Microsoft Docs"
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
  - "回転 (UIElements を)"
  - "UIElements, 回転"
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : UIElement を左右または上下に反転させる
この例では、<xref:System.Windows.Media.ScaleTransform> を使用して <xref:System.Windows.UIElement> を左右または上下に反転させる方法について説明します。  この例では、<xref:System.Windows.Controls.Button> コントロール \(<xref:System.Windows.UIElement> 型\) を、その <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに <xref:System.Windows.Media.ScaleTransform> を適用することによって反転します。  
  
## 使用例  
 次の図は、反転する対象のボタンを示しています。  
  
 ![変換のないボタン](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.png "graphicsmm\_buttonflipbeforeflip")  
反転対象の UIElement  
  
 ボタンを作成するコードを次に示します。  
  
 [!code-xml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## 使用例  
 ボタンを左右に反転するには、<xref:System.Windows.Media.ScaleTransform> を作成し、その <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> プロパティに \-1 を設定します。  この <xref:System.Windows.Media.ScaleTransform> をボタンの <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに適用します。  
  
 [!code-xml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![&#40;0,0&#41; の周りで水平方向に反転されるボタン](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.png "graphicsmm\_buttonfliphorizontalflip\_displaced")  
ScaleTransform を適用した後のボタン  
  
## 使用例  
 上の図を見るとわかるように、ボタンは反転しただけでなく、位置も変わりました。  これは、ボタンをその左上隅を中心に反転させたためです。  ボタンをその場で反転させるには、ボタンの隅ではなく中心に <xref:System.Windows.Media.ScaleTransform> を適用する必要があります。  <xref:System.Windows.Media.ScaleTransform> をボタンの中心に適用する簡単な方法は、ボタンの <xref:System.Windows.UIElement.RenderTransformOrigin%2A> プロパティを 0.5, 0.5 に設定することです。  
  
 [!code-xml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![中心の周りで水平方向に反転されるボタン](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.png "graphicsmm\_buttonfliphorizontalflip\_inplace")  
RenderTransformOrigin を 0.5, 0.5 に設定したボタン  
  
## 使用例  
 ボタンを上下に反転するには、<xref:System.Windows.Media.ScaleTransform> オブジェクトの <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> プロパティではなく <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> プロパティを設定します。  
  
 [!code-xml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![中心の周りで垂直方向に反転されるボタン](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.png "graphicsmm\_buttonflipverticalflip\_inplace")  
上下に反転させたボタン  
  
## 参照  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)