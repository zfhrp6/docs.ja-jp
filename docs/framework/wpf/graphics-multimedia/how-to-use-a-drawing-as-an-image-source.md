---
title: "方法 : 描画をイメージ ソースとして使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e100bc29afb17a37bc0c66621261347bea6d210
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>方法 : 描画をイメージ ソースとして使用する
この例を使用する方法を示しています、<xref:System.Windows.Media.Drawing>として、<xref:System.Windows.Controls.Image.Source%2A>の<xref:System.Windows.Controls.Image>コントロール。 表示する、<xref:System.Windows.Media.Drawing>で、<xref:System.Windows.Controls.Image>コントロールを使用して、<xref:System.Windows.Media.DrawingImage>として、<xref:System.Windows.Controls.Image>コントロールの<xref:System.Windows.Controls.Image.Source%2A>設定と、<xref:System.Windows.Media.DrawingImage>オブジェクトの<xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>プロパティを表示する描画をします。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.DrawingImage>と<xref:System.Windows.Controls.Image>を表示するコントロール、<xref:System.Windows.Media.GeometryDrawing>です。 この例を実行すると、次の出力が生成されます。  
  
 ![楕円 2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [ImageDrawing を使用してイメージを描画する](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions:Freeze 属性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
