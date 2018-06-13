---
title: '方法 : 複合描画を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: bb222fff11c81b491c0413f174539ff0005d11b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561594"
---
# <a name="how-to-create-a-composite-drawing"></a>方法 : 複合描画を作成する
この例を使用する方法を示しています、<xref:System.Windows.Media.DrawingGroup>複数を組み合わせることで複雑な図面を作成する<xref:System.Windows.Media.Drawing>に 1 つの複合描画オブジェクトです。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.DrawingGroup>の描画領域を作成する、<xref:System.Windows.Media.GeometryDrawing>と<xref:System.Windows.Media.ImageDrawing>オブジェクト。 次の図は、この例で生成される出力を示しています。  
  
 ![複数の描画を含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
DrawingGroup を使用して作成される複合描画  
  
 描画の境界を示しています。 灰色の枠線に注意してください。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 使用することができます、<xref:System.Windows.Media.DrawingGroup>を適用する、 <xref:System.Windows.Media.DrawingGroup.Transform%2A>、<xref:System.Windows.Media.DrawingGroup.Opacity%2A>設定、 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、または<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>が含まれている図面にします。 <xref:System.Windows.Media.DrawingGroup>も、 <xref:System.Windows.Media.Drawing>、他の含めることができます<xref:System.Windows.Media.DrawingGroup>オブジェクト。  
  
 追加を使用する点を除いて、次の例は前の例のような<xref:System.Windows.Media.DrawingGroup>の描いた絵の一部のビットマップ効果と不透明度マスクを適用するオブジェクト。 次の図は、この例で生成される出力を示しています。  
  
 ![複数の描画を含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")  
描画する複合が複数の DrawingGroup オブジェクト  
  
 描画の境界を示しています。 灰色の枠線に注意してください。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 詳細については<xref:System.Windows.Media.Drawing>、オブジェクトを参照してください[描画オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
