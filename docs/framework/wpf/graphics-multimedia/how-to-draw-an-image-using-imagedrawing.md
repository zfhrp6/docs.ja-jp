---
title: "方法 : ImageDrawing を使用してイメージを描画する | Microsoft Docs"
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
  - "クラス, ImageDrawing"
  - "描画, イメージ"
  - "グラフィックス, 描画 (イメージを)"
  - "ImageDrawing クラス"
  - "イメージ, 描画"
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : ImageDrawing を使用してイメージを描画する
この例では、<xref:System.Windows.Media.ImageDrawing> を使用してイメージを描画する方法を示します。  <xref:System.Windows.Media.ImageDrawing> では、<xref:System.Windows.Media.DrawingBrush>、<xref:System.Windows.Media.DrawingImage>、または <xref:System.Windows.Media.Visual> を使用して <xref:System.Windows.Media.ImageSource> を表示できます。  イメージを描画するには、<xref:System.Windows.Media.ImageDrawing> を作成して、その <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=fullName> プロパティと <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=fullName> プロパティを設定します。  <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=fullName> プロパティは描画するイメージを指定し、<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=fullName> プロパティは各イメージの位置とサイズを指定します。  
  
## 使用例  
 4 つの <xref:System.Windows.Media.ImageDrawing> オブジェクトを使用して 1 つの複合描画を作成する例を次に示します。  この例を実行すると、次のイメージが生成されます。  
  
 ![複数の DrawingImage オブジェクト](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.png "graphicsmm\_ImageDrawingExample")  
4 つの ImageDrawing オブジェクト  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <xref:System.Windows.Media.ImageDrawing> を使用せずにイメージを表示する簡単な方法の例については、「[イメージ要素を使用する](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Freezable.Freeze%2A>   
 <xref:System.Windows.Controls.Image>   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [PresentationOptions:Freeze 属性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)