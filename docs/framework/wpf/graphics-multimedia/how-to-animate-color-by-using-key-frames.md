---
title: "方法 : キー フレームを使用して色をアニメーション化する"
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
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d117d57e5cc761aa2f31fd6531bff8d96ea30dc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-color-by-using-key-frames"></a>方法 : キー フレームを使用して色をアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>キー フレームを使用しています。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.SolidColorBrush.Color%2A>のプロパティ、<xref:System.Windows.Media.SolidColorBrush>です。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.LinearColorKeyFrame>緑から赤に色を徐々 に変化するクラス。 などの線形のキー フレーム<xref:System.Windows.Media.Animation.LinearColorKeyFrame>値の間のスムーズな線形遷移を作成します。  
  
2.  インスタンスを使用している 0.5 秒は、次の終了時に、<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>すばやく赤から色を黄色に変更するクラス。 などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>されている値の間での急激な変化を作成、アニメーションのこの部分の色の変更が迅速に行われます、わずかではありません。  
  
3.  最後の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.SplineColorKeyFrame>色を変更する、もう一度クラス-現時点黄色から緑色にします。 スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineColorKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>プロパティです。 この例では、色の変化は最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
