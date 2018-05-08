---
title: '方法 : キー フレームを使用して Double 値をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 4adeb858ab1b69ef1b00f7bf3b6868dbcbbc4154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>方法 : キー フレームを使用して Double 値をアニメーション化する
この例を受け取るプロパティの値をアニメーション化する方法を示しています、<xref:System.Double>キー フレームを使用しています。  
  
## <a name="example"></a>例  
 次の例では、画面を横切るように四角形を移動します。 この例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、<xref:System.Windows.Media.TranslateTransform>に適用される、<xref:System.Windows.Shapes.Rectangle>です。 無期限に繰り返すこのアニメーションでは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 3 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>パスに沿った四角形の開始位置からの一定の割合で 500 の位置に移動するクラス。 などの線形のキー フレーム<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>値の間のスムーズな線形遷移を作成します。  
  
2.  4 番目の 2 つ目の末尾には、インスタンスを使用して、<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>突然四角形を次の位置に移動するクラス。 などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>値間の突然のジャンプを作成します。 この例では、開始位置にあった四角形が突然 500 の位置に出現します。  
  
3.  最後の 2 つの秒単位でのインスタンスを使用して、<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>四角形の開始位置に移動するクラス。 スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>プロパティです。 この例では、四角形の動きは最初はゆっくりしていますが、時間セグメントの終点に向かった急激に速くなります。  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
 この例のコードを使用して他のアニメーション例と一貫性を保つのため、<xref:System.Windows.Media.Animation.Storyboard>を適用するオブジェクト、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>です。 または、コード内の 1 つのアニメーションを適用するときに使いやすく、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用してではなく、<xref:System.Windows.Media.Animation.Storyboard>です。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
