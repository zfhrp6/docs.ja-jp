---
title: "方法 : パスに沿ってオブジェクトをアニメーション化する (オフセット累積による行列アニメーション) | Microsoft Docs"
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
  - "オフセット累積"
  - "アニメーション オブジェクトをパスに沿って (オフセット累積による行列アニメーション)"
  - "行列アニメーション (オフセット累積による)"
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : パスに沿ってオブジェクトをアニメーション化する (オフセット累積による行列アニメーション)
この例では、使用して、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>をパスに沿ってオブジェクトをアニメーション化し、そのオフセットを蓄積したアニメーション クラスに繰り返すような値です。  
  
## <a name="example"></a>例  
 次の例では、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、 <xref:System.Windows.Media.MatrixTransform>ボタンに適用します。 その結果、ボタンは、曲線のパスに沿って移動します。  
  
 さらに、例では、設定、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>プロパティを`true`、それが原因で、アニメーションを繰り返すたびに蓄積するアニメーション化された行列のオフセット。 オフセットが累積されるため、ボタンは開始位置にリセットするのではなく、アニメーションの繰り返し時に画面間で広く移動します。  
  
 [!code-xml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>プロパティと、繰り返しを累積するオフセット値を蓄積する回転の値が原因にはなりません。 回転の値を蓄積するために、設定、アニメーションの<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>と<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A>プロパティ`true`します。  
  
 完全なサンプルを参照してください。[パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)します。 アニメーション化する方法を示す例については、<xref:System.Windows.Media.Matrix>オフセット累積せずパスに沿った値を参照してください[オブジェクトに沿って、パス (行列アニメーション) をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)です。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)