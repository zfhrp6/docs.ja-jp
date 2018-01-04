---
title: "方法 : 楕円の円弧を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e11f3e0035c00bbc280b658c0931d57c37524f93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-elliptical-arc"></a>方法 : 楕円の円弧を作成する
この例では、楕円の円弧を描画する方法を示します。楕円の円弧を作成するには、使用、 <xref:System.Windows.Media.PathGeometry>、 <xref:System.Windows.Media.PathFigure>、および<xref:System.Windows.Media.ArcSegment>クラスです。  
  
## <a name="example"></a>例  
 次の例では、楕円の円弧は (10,100) から (200, 100) に描画されます。 円弧が、 <xref:System.Windows.Media.ArcSegment.Size%2A> 100 で 50 のデバイスに依存しないピクセル単位の<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>45 度、<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>の設定`true`、および<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>の<xref:System.Windows.Media.SweepDirection.Counterclockwise>します。  
  
 [xaml]  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]パスを記述する属性の構文を使用することができます。  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 (この属性の構文が実際に作成するメモ、 <xref:System.Windows.Media.StreamGeometry>、軽量バージョンの<xref:System.Windows.Media.PathGeometry>です。 詳細については、「[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)」のページを参照してください。)  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、明示的に object タグを使用して、楕円の円弧を描画することもできます。 次は、前と同じ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 この例は、さらに大きなサンプルの一部です。 サンプル全体については、次を参照してください。、[ジオメトリ サンプル](http://go.microsoft.com/fwlink/?LinkID=159989)です。  
  
## <a name="see-also"></a>参照  
 [2 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [3 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
