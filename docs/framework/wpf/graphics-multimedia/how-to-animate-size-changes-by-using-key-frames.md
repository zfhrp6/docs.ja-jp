---
title: "方法 : キー フレームを使用してサイズの変更をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30ee897efd01712bf4313da87e1050c5a16e4523
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="16b09-102">方法 : キー フレームを使用してサイズの変更をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="16b09-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="16b09-103">この例では、キー フレームを使用してサイズの変更をアニメーション化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="16b09-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16b09-104">例</span><span class="sxs-lookup"><span data-stu-id="16b09-104">Example</span></span>  
 <span data-ttu-id="16b09-105">次の例では、<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.ArcSegment.Size%2A>のプロパティ、<xref:System.Windows.Media.ArcSegment>です。</span><span class="sxs-lookup"><span data-stu-id="16b09-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="16b09-106">このアニメーションは、次の方法で 3 つのキー フレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="16b09-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="16b09-107">最初、0.5 秒、アニメーションの中のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>円弧のサイズが徐々 に増加するクラス。などの線形のキー フレーム<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>値の間のスムーズな線形遷移を作成します。</span><span class="sxs-lookup"><span data-stu-id="16b09-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="16b09-108">インスタンスを使用している 0.5 秒は、次の最後に、<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>円弧のサイズが突然増加するクラス。などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>されている値の間の突然のジャンプを作成、サイズの変更が突然発生して、微妙ではありません。</span><span class="sxs-lookup"><span data-stu-id="16b09-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3.  <span data-ttu-id="16b09-109">インスタンスが使用する最後の 2 秒、<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>円弧のサイズを大きくクラス。スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="16b09-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="16b09-110">この例では、円弧のサイズは最初はゆっくり大きくなりますが、時間セグメントの終点に向かって急激に大きくなります。</span><span class="sxs-lookup"><span data-stu-id="16b09-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="16b09-111">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16b09-111">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b09-112">参照</span><span class="sxs-lookup"><span data-stu-id="16b09-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [<span data-ttu-id="16b09-113">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="16b09-113">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="16b09-114">キー フレームに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="16b09-114">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
