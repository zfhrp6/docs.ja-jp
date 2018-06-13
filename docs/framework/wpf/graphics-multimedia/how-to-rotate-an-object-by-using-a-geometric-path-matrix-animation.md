---
title: '方法 : ジオメトリック パスを使用してオブジェクトを回転させる (行列アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 6deb593ca059d49f744226be313adb6d8781b325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561990"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>方法 : ジオメトリック パスを使用してオブジェクトを回転させる (行列アニメーション)
この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>と<xref:System.Windows.Media.MatrixTransform>(pivot) によって定義されたジオメトリック パスに沿ってオブジェクトを回転する、<xref:System.Windows.Media.PathGeometry>オブジェクト。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化するオブジェクト、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>です。 <xref:System.Windows.Media.MatrixTransform>ボタンに適用され、曲線のパスに沿って移動する場合は、します。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>プロパティに設定されている`true`、四角形がパスの接線に沿って回転します。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。  
  
 使用される前の例のコードのバージョン、<xref:System.Windows.Media.Animation.Storyboard>アニメーション化する、 <xref:System.Windows.Media.EllipseGeometry>1 つだけのアニメーションが適用された場合でも、します。 コードでは、プロパティに 1 つのアニメーションを適用する簡単な方法が使用するには、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドです。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)
