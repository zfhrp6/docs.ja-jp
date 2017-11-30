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
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="ba7c0-102">方法 : キー フレームを使用して境界線の太さをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="ba7c0-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="ba7c0-103">この例は、アニメーション化する方法を示しています、<xref:System.Windows.Controls.Control.BorderThickness%2A>のプロパティ、<xref:System.Windows.Controls.Border>です。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba7c0-104">例</span><span class="sxs-lookup"><span data-stu-id="ba7c0-104">Example</span></span>  
 <span data-ttu-id="ba7c0-105">次の例では、<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Controls.Control.BorderThickness%2A>のプロパティ、<xref:System.Windows.Controls.Border>です。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="ba7c0-106">このアニメーションは、次の方法で 3 つのキー フレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="ba7c0-107">最初の 0.5 秒中のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>クラスを境界線の太さを徐々 に増やします。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="ba7c0-108">この例では<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>値の間で滑らかな線形増加を作成します。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2.  <span data-ttu-id="ba7c0-109">インスタンスを使用している 0.5 秒は、次の最後に、<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>の境界線の太さを突然増加するクラス。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="ba7c0-110">派生したものと同様の個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>されている値の間の突然のジャンプを作成、アニメーションの動きがスムーズでないです。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3.  <span data-ttu-id="ba7c0-111">最後の 2 秒間には、インスタンスを使用して、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>の境界線の太さを削減するクラス。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="ba7c0-112">派生したものと同様の spline キー フレーム<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="ba7c0-113">このキー フレームでは、アニメーションはゆっくりと始まりますが、時間セグメントの終点に向かって急激に速くなります。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="ba7c0-114">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba7c0-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba7c0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba7c0-115">See Also</span></span>  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [<span data-ttu-id="ba7c0-116">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="ba7c0-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="ba7c0-117">キー フレームに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="ba7c0-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [<span data-ttu-id="ba7c0-118">BorderThickness 値をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="ba7c0-118">Animate a BorderThickness Value</span></span>](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
