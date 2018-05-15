---
title: '方法 : キー フレームを使用して文字列をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 5219ce11667c84d3ceca380d5a4ddd52695736b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="2faa7-102">方法 : キー フレームを使用して文字列をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="2faa7-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="2faa7-103">この例があり、この例では、文字列をアニメーション化する方法を示しています、<xref:System.Windows.Controls.ContentControl.Content%2A>のプロパティ、<xref:System.Windows.Controls.Button>キー フレームを使用して、コントロール。</span><span class="sxs-lookup"><span data-stu-id="2faa7-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2faa7-104">例</span><span class="sxs-lookup"><span data-stu-id="2faa7-104">Example</span></span>  
 <span data-ttu-id="2faa7-105">次の例では、<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Controls.ContentControl.Content%2A>のプロパティ、<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="2faa7-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="2faa7-106">この例ではすべてのキー フレームのインスタンスを使用して、<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>クラスため、キー フレームが作成される文字列のアニメーションは、個別のキー フレームにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2faa7-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="2faa7-107">などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>されている値の間の突然のジャンプを作成する、アニメーションへの変更が迅速に行うし、微妙ではありません。</span><span class="sxs-lookup"><span data-stu-id="2faa7-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="2faa7-108">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2faa7-108">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2faa7-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="2faa7-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [<span data-ttu-id="2faa7-110">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="2faa7-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="2faa7-111">キー フレームに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="2faa7-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
