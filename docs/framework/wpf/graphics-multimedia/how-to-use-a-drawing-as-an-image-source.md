---
title: '方法 : 描画をイメージ ソースとして使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: 7da8a2a594b0562667aaf417d736159d98818a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562291"
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
