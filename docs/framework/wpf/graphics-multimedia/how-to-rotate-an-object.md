---
title: "方法 : オブジェクトを回転させる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9b6212ed6c50faf73a6d3531f001a1b7e72d33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object"></a>方法 : オブジェクトを回転させる
次の例では、オブジェクトを回転させる方法を示します。 例では、最初に作成、<xref:System.Windows.Media.RotateTransform>し、その<xref:System.Windows.Media.RotateTransform.Angle%2A>(度単位)。  
  
 次の例では回転、 <xref:System.Windows.Shapes.Polyline> 45 度の左上隅のオブジェクトします。  
  
## <a name="example"></a>例  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>のプロパティ、<xref:System.Windows.Media.RotateTransform>オブジェクトの回転についてポイントを指定します。 この中心点は、変換する要素の座標空間で表します。 既定では、回転は (0,0) に適用されます。これは変換対象のオブジェクトの左上隅です。  
  
 次の例では回転、<xref:System.Windows.Shapes.Polyline>ポイント (25, 50) 時計回りに 45 度のオブジェクトします。  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 次の図に、適用した結果、 <xref:System.Windows.Media.Transform> 2 つのオブジェクトにします。  
  
 ![中心点が異なる 45 度の回転](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
異なる中心点を軸に 45 度回転させた 2 つのオブジェクト  
  
 <xref:System.Windows.Shapes.Polyline>前の例では、<xref:System.Windows.UIElement>です。 適用すると、<xref:System.Windows.Media.Transform>を<xref:System.Windows.UIElement.RenderTransform%2A>のプロパティ、 <xref:System.Windows.UIElement>、使用することができます、<xref:System.Windows.UIElement.RenderTransformOrigin%2A>の配信元を指定するプロパティすべて<xref:System.Windows.Media.Transform>要素に適用されます。 <xref:System.Windows.UIElement.RenderTransformOrigin%2A>プロパティが相対座標を使用して、そのサイズがわからない場合でも、要素の中心に、変換を適用することができます。 詳細と例についてを参照してください。[指定の相対値を使用して変換の原点](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)です。  
  
 完全なサンプルについては、「[2-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Transform>  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
