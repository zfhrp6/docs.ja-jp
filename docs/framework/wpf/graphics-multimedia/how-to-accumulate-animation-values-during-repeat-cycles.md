---
title: '方法 : 反復サイクル中にアニメーション値を累積する'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 7b954a388549f1bc6f3fa6ec1bcb2df61cc4e045
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557668"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="33465-102">方法 : 反復サイクル中にアニメーション値を累積する</span><span class="sxs-lookup"><span data-stu-id="33465-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="33465-103">この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>反復サイクル全体でアニメーションの値を累積するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="33465-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33465-104">例</span><span class="sxs-lookup"><span data-stu-id="33465-104">Example</span></span>  
 <span data-ttu-id="33465-105">使用して、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>反復サイクル全体でアニメーションの基本値を蓄積するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="33465-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="33465-106">たとえば、9 回繰り返して、アニメーションを設定する場合 (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> "9 x"=) 10 から 15 までアニメーション化するプロパティを設定して (= 10 = 15)、プロパティにアニメーションを付ける 10 から 15 サイクル中に、最初、15、2 つ目のサイクルの 20 ~、25 の間に、3 つ目のサイクルの 20 です。</span><span class="sxs-lookup"><span data-stu-id="33465-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="33465-107">そのため、各アニメーション サイクルは、その基本値として前のアニメーション サイクルの終了値を使用します。</span><span class="sxs-lookup"><span data-stu-id="33465-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="33465-108">使用することができます、`IsCumulative`最も基本的なアニメーションとほとんどのキー フレーム アニメーションのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="33465-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="33465-109">詳細については、次を参照してください。[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)と[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="33465-109">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="33465-110">次の例では、次の 4 つの四角形の幅をアニメーション化によってこの動作を示します。</span><span class="sxs-lookup"><span data-stu-id="33465-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="33465-111">例:</span><span class="sxs-lookup"><span data-stu-id="33465-111">The example:</span></span>  
  
-   <span data-ttu-id="33465-112">最初の四角形をアニメーション化<xref:System.Windows.Media.Animation.DoubleAnimation>設定と、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="33465-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="33465-113">含む 2 つ目の四角形をアニメーション化<xref:System.Windows.Media.Animation.DoubleAnimation>設定と、<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>プロパティの既定値を`false`です。</span><span class="sxs-lookup"><span data-stu-id="33465-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="33465-114">含む 3 つ目の四角形をアニメーション化<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>設定と、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="33465-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="33465-115">含む最後の四角形をアニメーション化<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>設定と、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="33465-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="33465-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="33465-116">See Also</span></span>  
 [<span data-ttu-id="33465-117">アニメーションの出力値をアニメーションの開始値に追加する</span><span class="sxs-lookup"><span data-stu-id="33465-117">Add an Animation Output Value to an Animation Starting Value</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [<span data-ttu-id="33465-118">アニメーションを反復する</span><span class="sxs-lookup"><span data-stu-id="33465-118">Repeat an Animation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [<span data-ttu-id="33465-119">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="33465-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="33465-120">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="33465-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="33465-121">方法トピック</span><span class="sxs-lookup"><span data-stu-id="33465-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
