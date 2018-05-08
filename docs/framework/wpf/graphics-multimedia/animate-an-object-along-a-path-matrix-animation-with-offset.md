---
title: '方法 : パスに沿ってオブジェクトをアニメーション化する (オフセット累積による行列アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 77daf4efb913f2bc2606247178b6a6c4add29bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>方法 : パスに沿ってオブジェクトをアニメーション化する (オフセット累積による行列アニメーション)
この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>クラスをパスに沿ってオブジェクトをアニメーション化し、そのオフセットを蓄積したアニメーションが繰り返される値します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>ボタンに適用します。 その結果、ボタンは曲線状のパスに沿って移動します。  
  
 さらに、例では、設定、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>プロパティを`true`、それが原因で、アニメーションを繰り返すたびに蓄積するアニメーション化された行列のオフセット。 オフセットが累積されるので、アニメーションが繰り返されたとき、ボタンは開始位置にリセットされるのではなく、画面を横切ってさらに移動します。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 なお、ですが、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>プロパティを繰り返しで累積する値をオフセットするとを蓄積する回転の値が原因です。 回転の値を蓄積するために、設定、アニメーションの<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>と<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A>プロパティ`true`です。  
  
 サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。 アニメーション化する方法を示す例については、<xref:System.Windows.Media.Matrix>オフセット累積せずパスに沿った値は、「[オブジェクトに沿って、パス (行列アニメーション) をアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)です。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
