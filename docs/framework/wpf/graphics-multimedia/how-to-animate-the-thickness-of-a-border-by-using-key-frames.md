---
title: "方法 : キー フレームを使用して境界線の太さをアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08950b2b92bfcbd28472327f12a2ee49abfd9fed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>方法 : キー フレームを使用して境界線の太さをアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Controls.Control.BorderThickness%2A>のプロパティ、<xref:System.Windows.Controls.Border>です。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Controls.Control.BorderThickness%2A>のプロパティ、<xref:System.Windows.Controls.Border>です。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 0.5 秒中のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>クラスを境界線の太さを徐々 に増やします。 この例では<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>値の間で滑らかな線形増加を作成します。  
  
2.  インスタンスを使用している 0.5 秒は、次の最後に、<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>の境界線の太さを突然増加するクラス。 派生したものと同様の個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>されている値の間の突然のジャンプを作成、アニメーションの動きがスムーズでないです。  
  
3.  最後の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>の境界線の太さを削減するクラス。 派生したものと同様の spline キー フレーム<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>プロパティです。 このキー フレームでは、アニメーションはゆっくりと始まりますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [BorderThickness 値をアニメーション化する](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
