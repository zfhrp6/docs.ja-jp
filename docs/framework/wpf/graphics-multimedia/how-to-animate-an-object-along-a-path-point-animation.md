---
title: "方法 : パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション) | Microsoft Docs"
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
  - "アニメーション オブジェクトをパスに沿って (ポイント アニメーション)"
  - "ポイント アニメーション"
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション)
この例では、使用、 <xref:System.Windows.Media.Animation.PointAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Point>曲線のパスに沿ったします。  
  
## <a name="example"></a>例  
 次の例では移動、 <xref:System.Windows.Media.EllipseGeometry>によって定義されたパスに沿った、 <xref:System.Windows.Media.PathGeometry>します。 楕円ジオメトリの<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティを<xref:System.Windows.Point>値してアニメーション化する楕円ジオメトリを移動する位置を指定するには、その<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティです。 例では、 <xref:System.Windows.Media.Animation.PointAnimationUsingPath>をアニメーション化する、 <xref:System.Windows.Media.EllipseGeometry>オブジェクトの<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティです。  
  
 [!code-xml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 完全なサンプルを参照してください。[パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)します。  
  
 使用前の例のコードのバージョン、<xref:System.Windows.Media.Animation.Storyboard>をアニメーション化する、 <xref:System.Windows.Media.EllipseGeometry>1 つだけのアニメーションが適用された場合でも、します。 A<xref:System.Windows.Media.Animation.Storyboard>同じによってこれらのアニメーションを制御できるため、複数のアニメーションを適用する最も簡単な方法は、多くの場合、<xref:System.Windows.Media.Animation.Storyboard>します。 ただし、簡単にコードを使用する場合は、1 つのアニメーションをプロパティに適用する方法が使用するは、 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドです。 例については、次を参照してください。[プロパティなしを使用して、ストーリー ボード アニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)です。  
  
## <a name="see-also"></a>関連項目  
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)