---
title: "方法 : パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション)"
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
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399d6b8028b8715f38335089a723707657df4a98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>方法 : パスに沿ってオブジェクトをアニメーション化する (ポイント アニメーション)
この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.PointAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Point>曲線のパスに沿ったです。  
  
## <a name="example"></a>例  
 次の例では移動、<xref:System.Windows.Media.EllipseGeometry>によって定義されたパスに沿った、<xref:System.Windows.Media.PathGeometry>です。 楕円のジオメトリの<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティを<xref:System.Windows.Point>値をアニメーション化する楕円のジオメトリを移動する; その位置を示すその<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティです。 この例では、<xref:System.Windows.Media.Animation.PointAnimationUsingPath>アニメーション化する、<xref:System.Windows.Media.EllipseGeometry>オブジェクトの<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティです。  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。  
  
 使用される前の例のコードのバージョン、<xref:System.Windows.Media.Animation.Storyboard>アニメーション化する、 <xref:System.Windows.Media.EllipseGeometry>1 つだけのアニメーションが適用された場合でも、します。 A<xref:System.Windows.Media.Animation.Storyboard>同じによってこれらのアニメーションを制御できるため、複数のアニメーションを適用する最も簡単な方法は、多くの場合、<xref:System.Windows.Media.Animation.Storyboard>です。 しかし、コードを使用するときに、プロパティに 1 つのアニメーションを適用する簡単な方法は、使用する、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドです。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
