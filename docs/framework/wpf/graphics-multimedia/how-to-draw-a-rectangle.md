---
title: '方法 : 四角形を描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 100f1a8062628e892e9a71b988bb2a8754ea6bad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561047"
---
# <a name="how-to-draw-a-rectangle"></a>方法 : 四角形を描画する
この例を使用して、四角形を描画する方法を示しています、<xref:System.Windows.Shapes.Rectangle>要素。  
  
 四角形を描画するには、作成、<xref:System.Windows.Shapes.Rectangle>要素を指定し、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>です。 四角形の内部を描画するには、次のように設定します。 その<xref:System.Windows.Shapes.Shape.Fill%2A>です。 四角形にアウトラインを与えるを使用してその<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>プロパティです。  
  
 角の丸い四角形を提供する、省略可能な指定<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>と<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>プロパティです。 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>と<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>プロパティ設定を四角形の角を丸めるに使用される楕円の x 軸と y 軸半径。  
  
 次の例では、次の 2 つ<xref:System.Windows.Shapes.Rectangle>で要素が描画、<xref:System.Windows.Controls.Canvas>です。 最初の四角形は、<xref:System.Windows.Media.Brushes.Blue%2A>内部です。 2 つ目の四角形、 <xref:System.Windows.Media.Brushes.Blue%2A> 、内部、<xref:System.Windows.Media.Brushes.Black%2A>アウトライン、および角の丸いです。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 この例を使用しますが、<xref:System.Windows.Controls.Canvas>を四角形を含むで使用できる長方形要素 (およびその他のすべての図形要素) いずれかの<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.Control>テキスト以外のコンテンツをサポートします。 実際、四角形は特にの部分の背景を提供するのに役立ちます<xref:System.Windows.Controls.Grid>パネルです。 例については、次を参照してください。、[テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)です。  
  
 この例より大きなサンプルの一部サンプル全体については、次を参照してください。[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Shapes.Rectangle>  
 [図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)
