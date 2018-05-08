---
title: '方法 : キー フレームを使用して行列をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: edb7074dffab23810872f4347f5339270af86bd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>方法 : キー フレームを使用して行列をアニメーション化する
この例は、アニメーション化する方法を示しています。、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>キー フレームを使用しています。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>です。 この例では、<xref:System.Windows.Media.MatrixTransform>の位置と外観を変換するオブジェクト、<xref:System.Windows.Controls.Button>です。  
  
 このアニメーションで使用される、<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>クラスの 2 つのキー フレームを作成して、次の処理に。  
  
1.  1 つ目をアニメーション化<xref:System.Windows.Media.Matrix>最初 0.2 秒間にします。 例の変更、<xref:System.Windows.Media.Matrix.M11%2A>と<xref:System.Windows.Media.Matrix.M12%2A>のプロパティ、<xref:System.Windows.Media.Matrix>です。 この変更により、引き伸ばされ、傾斜するボタンをクリックします。 例でも変更、<xref:System.Windows.Media.Matrix.OffsetX%2A>と<xref:System.Windows.Media.Matrix.OffsetY%2A>プロパティ、ボタンの位置を変更できるようにします。  
  
2.  2 番目をアニメーション化<xref:System.Windows.Media.Matrix>1.0 秒です。 ボタンは、ボタンが不要になった傾斜または拡張されていて、別の位置に移動します。  
  
3.  アニメーションを無限に繰り返されます。  
  
> [!NOTE]
>  派生するフレームのキー、<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>オブジェクト作成の値の間の急激なジャンプであり、アニメーションの動きがスムーズでないです。  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
