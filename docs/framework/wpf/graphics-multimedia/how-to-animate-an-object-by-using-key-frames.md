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
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="4468a-102">方法 : キー フレームを使用してオブジェクトをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="4468a-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="4468a-103">この例は、この例ではオブジェクトをアニメーション化する方法を示しています、<xref:System.Windows.Controls.Page.Background%2A>のプロパティ、<xref:System.Windows.Controls.Page>キー フレームを使用して、制御します。</span><span class="sxs-lookup"><span data-stu-id="4468a-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4468a-104">例</span><span class="sxs-lookup"><span data-stu-id="4468a-104">Example</span></span>  
 <span data-ttu-id="4468a-105">次の例では、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>を変更して、色をアニメーション化するクラス、<xref:System.Windows.Controls.Page.Background%2A>のプロパティ、<xref:System.Windows.Controls.Page>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4468a-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="4468a-106">この例のアニメーションは、一定の間隔で別の背景ブラシを変更します。</span><span class="sxs-lookup"><span data-stu-id="4468a-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="4468a-107">このアニメーションで使用される、 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 3 つの異なるキー フレームを作成するクラス。</span><span class="sxs-lookup"><span data-stu-id="4468a-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="4468a-108">アニメーションでは、キー フレームを使用して、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4468a-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="4468a-109">最初の 2 つ目の最後に、アニメーションのインスタンス、<xref:System.Windows.Media.LinearGradientBrush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="4468a-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="4468a-110">例では、このセクションでは、赤にオレンジ色に色が黄色から移行できるように、背景色に線形グラデーションが適用されます。</span><span class="sxs-lookup"><span data-stu-id="4468a-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="4468a-111">次の 2 つ目の最後に、アニメーションのインスタンス、<xref:System.Windows.Media.RadialGradientBrush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="4468a-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="4468a-112">例では、このセクションでは、色が白を黒に青から移行できるように、背景色に放射状グラデーションが適用されます。</span><span class="sxs-lookup"><span data-stu-id="4468a-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="4468a-113">3 番目の 2 つ目の最後に、アニメーションのインスタンス、<xref:System.Windows.Media.DrawingBrush>クラスです。</span><span class="sxs-lookup"><span data-stu-id="4468a-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="4468a-114">例では、このセクションでは、バック グラウンドに、チェッカー ボード パターンを適用します。</span><span class="sxs-lookup"><span data-stu-id="4468a-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="4468a-115">アニメーションは、もう一度が開始され、無限に繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="4468a-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4468a-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>使用できるキー フレームの唯一の種類には、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>クラスです。</span><span class="sxs-lookup"><span data-stu-id="4468a-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="4468a-117">キー フレームのような<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>急激な変化で作成、値は、この例では色の変更が突然発生します。</span><span class="sxs-lookup"><span data-stu-id="4468a-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="4468a-118">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4468a-118">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4468a-119">参照</span><span class="sxs-lookup"><span data-stu-id="4468a-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [<span data-ttu-id="4468a-120">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="4468a-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="4468a-121">キー フレームに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="4468a-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
