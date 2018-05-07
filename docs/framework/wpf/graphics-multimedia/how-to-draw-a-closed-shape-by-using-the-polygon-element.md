---
title: '方法 : 多角形要素を使用して、閉じた図形を描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 4105139e159783cf0197f4e56c82001835077cbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>方法 : 多角形要素を使用して、閉じた図形を描画する
この例を使用して、閉じた図形を描画する方法を示しています、<xref:System.Windows.Shapes.Polygon>要素。 閉じた図形を描画するには、作成、<xref:System.Windows.Shapes.Polygon>要素とを使用してその<xref:System.Windows.Shapes.Polygon.Points%2A>図形の頂点を指定するプロパティです。 行を最初と最後のポイントに接続するには自動的には描画されます。 最後に、指定、 <xref:System.Windows.Shapes.Shape.Fill%2A>、 <xref:System.Windows.Shapes.Shape.Stroke%2A>、またはその両方です。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ポイントの有効な構文がコンマで区切った x 座標と y 座標の組のスペースで区切られた一覧を示します。  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 例を使用しますが、<xref:System.Windows.Controls.Canvas>を多角形を含むで使用できる多角形要素 (およびその他のすべての図形要素) いずれかの<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.Control>テキスト以外のコンテンツをサポートします。  
  
 この例より大きなサンプルの一部サンプル全体については、次を参照してください。[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)です。
