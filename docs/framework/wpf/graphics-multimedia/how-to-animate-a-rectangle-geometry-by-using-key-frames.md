---
title: "方法 : キー フレームを使用して四角形のジオメトリをアニメーション化する"
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
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6c23f894b6fa93a3889356416bd95f61fff8beb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>方法 : キー フレームを使用して四角形のジオメトリをアニメーション化する
この例は、アニメーション化する方法を示しています。、<xref:System.Windows.Media.RectangleGeometry.Rect%2A>のプロパティ、<xref:System.Windows.Media.RectangleGeometry>キー フレームを使用しています。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.RectangleGeometry.Rect%2A>のプロパティ、<xref:System.Windows.Media.RectangleGeometry>です。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.LinearRectKeyFrame>位置、幅、および四角形の高さの段階的な変更をアニメーション化するクラス。 などの線形のキー フレーム<xref:System.Windows.Media.Animation.LinearRectKeyFrame>値の間のスムーズな線形遷移を作成します。  
  
2.  インスタンスを使用している 0.5 秒は、次の終了時に、<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>突然四角形の高さを低くクラス。 などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>されている値の間での急激な変化を作成、高さの減少が迅速に行われ、微妙ではありません。  
  
3.  最後の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.SplineRectKeyFrame>四角形を元の位置とサイズに変更するクラス。 スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineRectKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A>プロパティです。 この例では、変化は最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
