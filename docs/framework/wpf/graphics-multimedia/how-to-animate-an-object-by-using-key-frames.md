---
title: "方法 : キー フレームを使用してオブジェクトをアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f513cda540b3337f1510ee0c46419a12023bcb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>方法 : キー フレームを使用してオブジェクトをアニメーション化する
この例は、この例ではオブジェクトをアニメーション化する方法を示しています、<xref:System.Windows.Controls.Page.Background%2A>のプロパティ、<xref:System.Windows.Controls.Page>キー フレームを使用して、制御します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>を変更して、色をアニメーション化するクラス、<xref:System.Windows.Controls.Page.Background%2A>のプロパティ、<xref:System.Windows.Controls.Page>コントロール。 この例のアニメーションは、一定の間隔で別の背景ブラシを変更します。 このアニメーションで使用される、 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 3 つの異なるキー フレームを作成するクラス。 アニメーションでは、キー フレームを使用して、次のようにします。  
  
1.  最初の 2 つ目の最後に、アニメーションのインスタンス、<xref:System.Windows.Media.LinearGradientBrush>クラスです。 例では、このセクションでは、赤にオレンジ色に色が黄色から移行できるように、背景色に線形グラデーションが適用されます。  
  
2.  次の 2 つ目の最後に、アニメーションのインスタンス、<xref:System.Windows.Media.RadialGradientBrush>クラスです。 例では、このセクションでは、色が白を黒に青から移行できるように、背景色に放射状グラデーションが適用されます。  
  
3.  3 番目の 2 つ目の最後に、アニメーションのインスタンス、<xref:System.Windows.Media.DrawingBrush>クラスです。 例では、このセクションでは、バック グラウンドに、チェッカー ボード パターンを適用します。  
  
4.  アニメーションは、もう一度が開始され、無限に繰り返されます。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>使用できるキー フレームの唯一の種類には、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>クラスです。 キー フレームのような<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>急激な変化で作成、値は、この例では色の変更が突然発生します。  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
