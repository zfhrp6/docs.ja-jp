---
title: '方法 : キー フレームを使用してブール値をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: d6273c08881e802595e831cafe120a5bec841c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556927"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="d4553-102">方法 : キー フレームを使用してブール値をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="d4553-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="d4553-103">この例のブール型プロパティ値をアニメーション化する方法を示しています、<xref:System.Windows.Controls.Button>キー フレームを使用して制御します。</span><span class="sxs-lookup"><span data-stu-id="d4553-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4553-104">例</span><span class="sxs-lookup"><span data-stu-id="d4553-104">Example</span></span>  
 <span data-ttu-id="d4553-105">次の例では、<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.UIElement.IsEnabled%2A>のプロパティ、<xref:System.Windows.Controls.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d4553-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="d4553-106">この例ではすべてのキー フレームのインスタンスを使用して、<xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d4553-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="d4553-107">などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame>されている値の間の突然のジャンプを作成、アニメーションの動きがスムーズでないです。</span><span class="sxs-lookup"><span data-stu-id="d4553-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="d4553-108">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4553-108">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4553-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4553-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>  
 <xref:System.Windows.UIElement.IsEnabled%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="d4553-110">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="d4553-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="d4553-111">キー フレームに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="d4553-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
