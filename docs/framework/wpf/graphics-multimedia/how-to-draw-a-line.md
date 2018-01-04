---
title: "方法 : 線を描画する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88d667e8654f72226dc609a14aec650effe2d5c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line"></a>方法 : 線を描画する
この例を使用して線を描画する方法を示します、<xref:System.Windows.Shapes.Line>要素。  
  
 線を描画するには、作成、<xref:System.Windows.Shapes.Line>要素。 使用してその<xref:System.Windows.Shapes.Line.X1%2A>と<xref:System.Windows.Shapes.Line.Y1%2A>; 始点を設定して使用するプロパティの<xref:System.Windows.Shapes.Line.X2%2A>と<xref:System.Windows.Shapes.Line.Y2%2A>終了点を設定するプロパティです。 最後に、設定、<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>線なしの行が表示されないためです。  
  
 設定、<xref:System.Windows.Shapes.Shape.Fill%2A>行の要素も何も起こりません、行には、内部があるないためです。  
  
 次の例は、内の次の 3 つの線を描画する<xref:System.Windows.Controls.Canvas>要素。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 この例より大きなサンプルの一部サンプル全体については、次を参照してください。[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Shapes.Line>  
 [図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)
