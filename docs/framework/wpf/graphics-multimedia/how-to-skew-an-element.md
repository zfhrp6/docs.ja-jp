---
title: "方法 : 要素を傾斜させる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5c46b8c64a26d83ba6d8f018b9a1f8ca8250a57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-skew-an-element"></a>方法 : 要素を傾斜させる
この例を使用する方法を示しています、<xref:System.Windows.Media.SkewTransform>要素を傾けるにします。 傾斜 (スキューと呼ばれることもあります) は、一様でない方法で座標空間を拡大する変換です。 一般的な用途の 1 つ、<xref:System.Windows.Media.SkewTransform>をシミュレートするため、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]で深さ[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]オブジェクト。  
  
 使用して、<xref:System.Windows.Media.SkewTransform.CenterX%2A>と<xref:System.Windows.Media.SkewTransform.CenterY%2A>のポイントを中心に指定のプロパティ、<xref:System.Windows.Media.SkewTransform>です。  
  
 使用して、<xref:System.Windows.Media.SkewTransform.AngleX%2A>と<xref:System.Windows.Media.SkewTransform.AngleY%2A>プロパティを x 軸と y 軸の傾斜角度を指定し、現在の座標系これらの軸に沿った傾斜をします。  
  
 傾斜変換の効果を予測することを検討<xref:System.Windows.Media.SkewTransform.AngleX%2A>元の座標システムに対して相対的な x 軸の値のずれ。 そのため、 <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30、y 軸原点を 30 度回転し、傾斜 x-30 ° を原点からの値。 同様に、 <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 の原点から 30 度、図形の y 値のずれ。 これは、座標系の x または y での 30 度の平行移動 (移動) と同じ効果はないことに注意してください。  
  
 次の例に 45 度の水平方向の傾斜を適用する、 <xref:System.Windows.Shapes.Rectangle> (0, 0) の中心点からです。  
  
## <a name="example"></a>例  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 次の例に 45 度の水平方向の傾斜を適用する、 <xref:System.Windows.Shapes.Rectangle> (25,25) の中心点からです。  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 次の例に 45 度の垂直方向の傾斜を適用する、 <xref:System.Windows.Shapes.Rectangle> (25,25) の中心点からです。  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 次の図は、この例で使用されている各種の傾斜を示しています。  
  
 ![SkewTransform の例](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
説明した 3 つの SkewTransform の例  
  
 完全なサンプルについては、「[2-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
