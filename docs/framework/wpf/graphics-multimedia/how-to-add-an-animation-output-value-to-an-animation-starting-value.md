---
title: "方法 : アニメーションの出力値をアニメーションの開始値に追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1a6a5923655c5857b813df778b36b6c7fd208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="0d91a-102">方法 : アニメーションの出力値をアニメーションの開始値に追加する</span><span class="sxs-lookup"><span data-stu-id="0d91a-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="0d91a-103">この例では、アニメーションの開始値をアニメーションの出力値を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0d91a-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d91a-104">例</span><span class="sxs-lookup"><span data-stu-id="0d91a-104">Example</span></span>  
 <span data-ttu-id="0d91a-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>プロパティをアニメーション化されたプロパティの開始値 (基本値) に追加されるアニメーションの出力値にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d91a-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="0d91a-106">使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>最も基本的なアニメーションとほとんどのキー フレーム アニメーションのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0d91a-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="0d91a-107">詳細については、次を参照してください。[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)と[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d91a-107">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="0d91a-108">次の例を使用しての効果を示しています、<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType>を持つプロパティ<xref:System.Windows.Media.Animation.DoubleAnimation>を使用して、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType>を持つプロパティ<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>です。</span><span class="sxs-lookup"><span data-stu-id="0d91a-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0d91a-109">参照</span><span class="sxs-lookup"><span data-stu-id="0d91a-109">See Also</span></span>  
 [<span data-ttu-id="0d91a-110">反復サイクル中にアニメーション値を累積する</span><span class="sxs-lookup"><span data-stu-id="0d91a-110">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="0d91a-111">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="0d91a-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="0d91a-112">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="0d91a-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="0d91a-113">アニメーションおよびタイミング</span><span class="sxs-lookup"><span data-stu-id="0d91a-113">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="0d91a-114">方法トピック</span><span class="sxs-lookup"><span data-stu-id="0d91a-114">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
