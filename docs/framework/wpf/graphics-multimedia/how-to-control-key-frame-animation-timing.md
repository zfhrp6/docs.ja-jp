---
title: '方法 : キー フレーム アニメーションのタイミングを制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 7aacb975557a25b8ea7a80e02c16a59b8a746e26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562298"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="796e5-102">方法 : キー フレーム アニメーションのタイミングを制御する</span><span class="sxs-lookup"><span data-stu-id="796e5-102">How to: Control Key-Frame Animation Timing</span></span>
<span data-ttu-id="796e5-103">この例では、キー フレーム アニメーション内のキー フレームのタイミングを制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="796e5-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="796e5-104">キー フレーム アニメーションにあるその他のアニメーションと同様に、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="796e5-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="796e5-105">アニメーションの duration を指定するだけでなくその期間のどの部分がそのキー フレームのそれぞれに割り当てられているを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="796e5-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="796e5-106">指定した時間を割り当てる、<xref:System.Windows.Media.Animation.KeyTime>の各キー フレーム アニメーションにします。</span><span class="sxs-lookup"><span data-stu-id="796e5-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>  
  
 <span data-ttu-id="796e5-107"><xref:System.Windows.Media.Animation.KeyTime>の (は指定しませんキー フレームの再生時間の長さ) のキー フレームの終了時に、各キー フレームを指定します。</span><span class="sxs-lookup"><span data-stu-id="796e5-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="796e5-108">指定することができます、<xref:System.Windows.Media.Animation.KeyTime>として、<xref:System.TimeSpan>値、パーセンテージ、または、<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>または<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>特殊な値です。</span><span class="sxs-lookup"><span data-stu-id="796e5-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="796e5-109">例</span><span class="sxs-lookup"><span data-stu-id="796e5-109">Example</span></span>  
 <span data-ttu-id="796e5-110">次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>を四角形を画面にアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="796e5-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="796e5-111">キー フレームのキー時刻が設定されて<xref:System.TimeSpan>値。</span><span class="sxs-lookup"><span data-stu-id="796e5-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 <span data-ttu-id="796e5-112">次の図の各キー フレームの値に達したときにします。</span><span class="sxs-lookup"><span data-stu-id="796e5-112">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="796e5-113">![キーの値が 3、4、および 10 秒の位置に到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="796e5-113">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>  
  
 <span data-ttu-id="796e5-114">次の例では、パーセンテージの値でキー フレームのキー時刻を設定する点を除いて同じですが、あるアニメーションを示します。</span><span class="sxs-lookup"><span data-stu-id="796e5-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 <span data-ttu-id="796e5-115">次の図の各キー フレームの値に達したときにします。</span><span class="sxs-lookup"><span data-stu-id="796e5-115">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="796e5-116">![キーの値が 3、4、および 10 秒の位置に到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="796e5-116">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>  
  
 <span data-ttu-id="796e5-117">次の例では<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>キー時刻値。</span><span class="sxs-lookup"><span data-stu-id="796e5-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 <span data-ttu-id="796e5-118">次の図の各キー フレームの値に達したときにします。</span><span class="sxs-lookup"><span data-stu-id="796e5-118">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="796e5-119">![キーの値に達した 3.3、6.6、および 9.9 秒](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="796e5-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>  
  
 <span data-ttu-id="796e5-120">最後の例を使用して<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>キー時刻値。</span><span class="sxs-lookup"><span data-stu-id="796e5-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 <span data-ttu-id="796e5-121">次の図の各キー フレームの値に達したときにします。</span><span class="sxs-lookup"><span data-stu-id="796e5-121">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="796e5-122">![キーの値が 0、5、および 10 秒の位置に到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="796e5-122">![Key values are reached at 0, 5, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>  
  
 <span data-ttu-id="796e5-123">わかりやすくするため、コードでは、この例を使用してローカル、アニメーションのないストーリー ボードを 1 つのプロパティを 1 つのアニメーションが適用されているが、ストーリー ボードを代わりに使用する例を変更する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="796e5-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="796e5-124">コード内のストーリー ボードを宣言する方法を示す例は、次を参照してください。[ストーリー ボードを使用してプロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)です。</span><span class="sxs-lookup"><span data-stu-id="796e5-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="796e5-125">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="796e5-125">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span> <span data-ttu-id="796e5-126">キー フレーム アニメーションの詳細については、次を参照してください。、[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="796e5-126">For more information about key frame animations, see the [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796e5-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="796e5-127">See Also</span></span>  
 [<span data-ttu-id="796e5-128">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="796e5-128">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="796e5-129">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="796e5-129">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="796e5-130">方法トピック</span><span class="sxs-lookup"><span data-stu-id="796e5-130">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
