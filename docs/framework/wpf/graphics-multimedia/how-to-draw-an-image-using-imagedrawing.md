---
title: "方法 : ImageDrawing を使用してイメージを描画する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d292617ef18bea32396327fd1b0a1d08d35ee16f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>方法 : ImageDrawing を使用してイメージを描画する
この例を使用する方法を示しています、<xref:System.Windows.Media.ImageDrawing>イメージを描画します。 <xref:System.Windows.Media.ImageDrawing>を表示できるように、<xref:System.Windows.Media.ImageSource>で、 <xref:System.Windows.Media.DrawingBrush>、 <xref:System.Windows.Media.DrawingImage>、または<xref:System.Windows.Media.Visual>です。 イメージを描画するを作成する、<xref:System.Windows.Media.ImageDrawing>設定とその<xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>と<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>プロパティです。 <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>プロパティを描画するイメージを指定して、<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>プロパティは、各イメージのサイズと位置を指定します。  
  
## <a name="example"></a>例  
 次の例では、次の 4 つを使用して複合描画<xref:System.Windows.Media.ImageDrawing>オブジェクト。 この例では、次の図が生成されます。  
  
 ![複数の DrawingImage オブジェクト](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
4 つの ImageDrawing オブジェクト  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 使用せずにイメージを表示する簡単な方法を示す例については<xref:System.Windows.Media.ImageDrawing>を参照してください[イメージ要素を使用して](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions:Freeze 属性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
