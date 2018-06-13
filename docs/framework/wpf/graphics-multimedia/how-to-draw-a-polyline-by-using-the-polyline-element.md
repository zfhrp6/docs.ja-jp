---
title: '方法 : ポリライン要素を使用してポリラインを描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 2abfa29f7aca4bfc8c5f91e36fd974093a98a9e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561762"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>方法 : ポリライン要素を使用してポリラインを描画する
この例を使用して、接続されている行の系列は、多角形を描画する方法を示しています、<xref:System.Windows.Shapes.Polyline>要素。  
  
 多角形を描画するには、作成、<xref:System.Windows.Shapes.Polyline>要素とを使用してその<xref:System.Windows.Shapes.Polyline.Points%2A>図形の頂点を指定するプロパティです。 最後に、使用して、<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>線なしの行が表示されていないため、多角形を記述するプロパティの概要です。  
  
> [!NOTE]
>  <xref:System.Windows.Shapes.Polyline>要素は、閉じた図形ではありません、<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティも何も起こりません、図形の輪郭を意図的に閉じた場合でもです。 閉じられたと図形を作成する、<xref:System.Windows.Shapes.Shape.Fill%2A>を使用して、<xref:System.Windows.Shapes.Polygon>要素。  
  
 次の例では、2 つの描画<xref:System.Windows.Shapes.Polyline>内の要素、<xref:System.Windows.Controls.Canvas>です。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ポイントの有効な構文がコンマで区切った x 座標と y 座標の組のスペースで区切られた一覧を示します。  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 この例を使用しますが、 <xref:System.Windows.Controls.Canvas> 、多角形を含むで使用できるポリライン要素 (およびその他のすべての図形要素) いずれかの<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.Control>テキスト以外のコンテンツをサポートします。  
  
 この例より大きなサンプルの一部サンプル全体については、次を参照してください。[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
