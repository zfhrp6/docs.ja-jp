---
title: "方法 : 直線または線分の終点のキャップを変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e062b82e698a99705a2b06588aa9aae3a0c93157
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>方法 : 直線または線分の終点のキャップを変更する
この例は、開始のまたは末尾に、開いている図形を変更する方法を示します<xref:System.Windows.Shapes.Shape>要素。 開いているの先頭に cap を変更する<xref:System.Windows.Shapes.Shape>を使用してその<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>プロパティです。 開いているの最後に、cap を変更する<xref:System.Windows.Shapes.Shape>を使用してその<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>プロパティです。 使用可能なライン キャップを表示するを参照してください。、<xref:System.Windows.Media.PenLineCap>列挙します。  
  
> [!NOTE]
>  このプロパティは、開いている図形など、 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Polyline>、または開いている<xref:System.Windows.Shapes.Path>要素。  
  
 次の例では、次の 4 つを描画<xref:System.Windows.Shapes.Polyline>要素の各端に別の図形のセットを使用しています。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 この例より大きなサンプルの一部サンプル全体については、次を参照してください。[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
