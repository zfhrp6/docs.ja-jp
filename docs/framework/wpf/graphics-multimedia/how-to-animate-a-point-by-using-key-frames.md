---
title: "方法 : キー フレームを使用して点をアニメーション化する"
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
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c115d31c6ace26f8fd9dd6cff3fdeead89eea33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>方法 : キー フレームを使用して点をアニメーション化する
この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Point>です。  
  
## <a name="example"></a>例  
 次の例では、三角形のパスに沿って楕円を移動します。 この例では、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.EllipseGeometry.Center%2A>のプロパティ、<xref:System.Windows.Media.EllipseGeometry>です。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 0.5 秒中のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearPointKeyFrame>の開始位置から一定の割合でパスに沿った楕円を移動するクラス。 などの線形のキー フレーム<xref:System.Windows.Media.Animation.LinearPointKeyFrame>値の間のスムーズな線形補間を作成します。  
  
2.  インスタンスを使用している 0.5 秒は、次の終了時に、<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>突然パスに沿った楕円を次の位置に移動するクラス。 などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>値間の突然のジャンプを作成します。  
  
3.  最後の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.SplinePointKeyFrame>楕円の開始位置に移動するクラス。 スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplinePointKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>プロパティです。 この例では、アニメーションは最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
 この例のコードを使用して他のアニメーション例と一貫性を保つのため、<xref:System.Windows.Media.Animation.Storyboard>を適用するオブジェクト、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>です。 ただし、コード内の 1 つのアニメーションを適用するときに使いやすく、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用してではなく、<xref:System.Windows.Media.Animation.Storyboard>です。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
