---
title: "方法 : 楕円の円弧を作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "円弧, 楕円"
  - "楕円の円弧, 作成"
  - "グラフィックス [WPF], 楕円の円弧"
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 楕円の円弧を作成する
この例では、楕円の円弧を描画する方法を示します。  楕円の円弧を作成するには、<xref:System.Windows.Media.PathGeometry>、<xref:System.Windows.Media.PathFigure>、および <xref:System.Windows.Media.ArcSegment> の各クラスを使用します。  
  
## 使用例  
 次の例では、\(10,100\) から \(200,100\) までの範囲に楕円の円弧を描画します。  この円弧は、<xref:System.Windows.Media.ArcSegment.Size%2A> が 100 × 50 デバイス非依存ピクセル、<xref:System.Windows.Media.ArcSegment.RotationAngle%2A> が 45°、<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> が `true`、<xref:System.Windows.Media.ArcSegment.SweepDirection%2A> が <xref:System.Windows.Media.SweepDirection> にそれぞれ設定されます。  
  
 \[xaml\]  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、属性の構文を使用してパスを記述できます。  
  
 [!code-xml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 \[xaml\]  
  
 \(この属性構文は、実際には <xref:System.Windows.Media.PathGeometry> の軽量バージョンである <xref:System.Windows.Media.StreamGeometry> を作成します。  詳細については、「[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)」のページを参照してください。\)  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、明示的にオブジェクト タグを使用して楕円の円弧を描画することもできます。  次に示す例は、前の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップと同等です。  
  
 [!code-xml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 この例は、より大きなサンプルの一部です。  サンプル全体については、[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)を参照してください。  
  
## 参照  
 [2 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)   
 [3 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)