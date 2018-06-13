---
title: '方法 : ストーリーボードを使用してアニメーション化した後にプロパティを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: b8e9c08075b13f8d6f701d5ac6ae4f8ea8949184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562266"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="22db6-102">方法 : ストーリーボードを使用してアニメーション化した後にプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="22db6-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="22db6-103">場合によっては、アニメーション化された後、プロパティの値を変更することはできません、ことがあります。</span><span class="sxs-lookup"><span data-stu-id="22db6-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22db6-104">例</span><span class="sxs-lookup"><span data-stu-id="22db6-104">Example</span></span>  
 <span data-ttu-id="22db6-105">次の例で、<xref:System.Windows.Media.Animation.Storyboard>の色をアニメーション化するために使用する<xref:System.Windows.Media.SolidColorBrush>です。</span><span class="sxs-lookup"><span data-stu-id="22db6-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="22db6-106">ストーリー ボードは、ボタンがクリックされたときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="22db6-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="22db6-107"><xref:System.Windows.Media.Animation.Timeline.Completed>プログラムが通知されるように、イベントが処理されるときに、<xref:System.Windows.Media.Animation.ColorAnimation>が完了します。</span><span class="sxs-lookup"><span data-stu-id="22db6-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="22db6-108">例</span><span class="sxs-lookup"><span data-stu-id="22db6-108">Example</span></span>  
 <span data-ttu-id="22db6-109">後に、<xref:System.Windows.Media.Animation.ColorAnimation>が完了したら、ブラシの色を青に変更を試行するプログラムです。</span><span class="sxs-lookup"><span data-stu-id="22db6-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="22db6-110">何も操作する前のコードが表示されない: によって提供される、ブラシは黄、これは、値、<xref:System.Windows.Media.Animation.ColorAnimation>ブラシをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="22db6-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="22db6-111">基になるプロパティの値 (基本値) は実際に青に変更されています。</span><span class="sxs-lookup"><span data-stu-id="22db6-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="22db6-112">ただし、有効なつまり現在の値は黄色ため、<xref:System.Windows.Media.Animation.ColorAnimation>底の値を上書きしています。</span><span class="sxs-lookup"><span data-stu-id="22db6-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="22db6-113">ベース値に有効な値をもう一度になる場合は、プロパティへの影響からアニメーションを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22db6-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="22db6-114">これにはストーリー ボードのアニメーションで行うには次の 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="22db6-114">There are three ways to do this with storyboard animations:</span></span>  
  
-   <span data-ttu-id="22db6-115">アニメーションの<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティ <xref:System.Windows.Media.Animation.FillBehavior.Stop></span><span class="sxs-lookup"><span data-stu-id="22db6-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to <xref:System.Windows.Media.Animation.FillBehavior.Stop></span></span>  
  
-   <span data-ttu-id="22db6-116">ストーリー ボード全体を削除します。</span><span class="sxs-lookup"><span data-stu-id="22db6-116">Remove the entire Storyboard.</span></span>  
  
-   <span data-ttu-id="22db6-117">アニメーションを個々 のプロパティから削除します。</span><span class="sxs-lookup"><span data-stu-id="22db6-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="22db6-118">Stop に設定されて、アニメーションの FillBehavior プロパティ</span><span class="sxs-lookup"><span data-stu-id="22db6-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="22db6-119">設定して<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>に<xref:System.Windows.Media.Animation.FillBehavior.Stop>、停止、アクティブな期間の末尾に達した後、ターゲット プロパティに影響を与えずに、アニメーションがわかります。</span><span class="sxs-lookup"><span data-stu-id="22db6-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="22db6-120">ストーリー ボード全体を削除します。</span><span class="sxs-lookup"><span data-stu-id="22db6-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="22db6-121">使用して、<xref:System.Windows.Media.Animation.RemoveStoryboard>トリガーまたは<xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>メソッド、そのターゲット プロパティの影響を与えることを停止するストーリー ボードのアニメーションがわかります。</span><span class="sxs-lookup"><span data-stu-id="22db6-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="22db6-122">このアプローチと設定の違い、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティは、ストーリー ボードを削除することでいつでも、while、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティにのみ影響アニメーションがアクティブな期間の最後に達するとします。</span><span class="sxs-lookup"><span data-stu-id="22db6-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="22db6-123">アニメーションを個々 のプロパティから削除します。</span><span class="sxs-lookup"><span data-stu-id="22db6-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="22db6-124">プロパティに影響を与えないアニメーションを停止するもう 1 つの方法は、使用する、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>アニメーション化されているオブジェクトのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="22db6-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="22db6-125">最初のパラメーターとしてアニメーション化されているプロパティを指定し、 `null` 2 つ目として。</span><span class="sxs-lookup"><span data-stu-id="22db6-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="22db6-126">この手法は、非ストーリー ボードのアニメーションのでも動作します。</span><span class="sxs-lookup"><span data-stu-id="22db6-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22db6-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="22db6-127">See Also</span></span>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [<span data-ttu-id="22db6-128">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="22db6-128">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="22db6-129">プロパティ アニメーションの手法の概要</span><span class="sxs-lookup"><span data-stu-id="22db6-129">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
