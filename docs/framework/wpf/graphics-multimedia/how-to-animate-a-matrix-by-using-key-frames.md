---
title: "方法 : キー フレームを使用して行列をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 862e1afdcd823181dff0948fab43b1656b85f721
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="f91a8-102">方法 : キー フレームを使用して行列をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="f91a8-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="f91a8-103">この例は、アニメーション化する方法を示しています。、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>キー フレームを使用しています。</span><span class="sxs-lookup"><span data-stu-id="f91a8-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f91a8-104">例</span><span class="sxs-lookup"><span data-stu-id="f91a8-104">Example</span></span>  
 <span data-ttu-id="f91a8-105">次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティ、<xref:System.Windows.Media.MatrixTransform>です。</span><span class="sxs-lookup"><span data-stu-id="f91a8-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="f91a8-106">この例では、<xref:System.Windows.Media.MatrixTransform>の位置と外観を変換するオブジェクト、<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="f91a8-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="f91a8-107">このアニメーションで使用される、<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>クラスの 2 つのキー フレームを作成して、次の処理に。</span><span class="sxs-lookup"><span data-stu-id="f91a8-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1.  <span data-ttu-id="f91a8-108">1 つ目をアニメーション化<xref:System.Windows.Media.Matrix>最初 0.2 秒間にします。</span><span class="sxs-lookup"><span data-stu-id="f91a8-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="f91a8-109">例の変更、<xref:System.Windows.Media.Matrix.M11%2A>と<xref:System.Windows.Media.Matrix.M12%2A>のプロパティ、<xref:System.Windows.Media.Matrix>です。</span><span class="sxs-lookup"><span data-stu-id="f91a8-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="f91a8-110">この変更により、引き伸ばされ、傾斜するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f91a8-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="f91a8-111">例でも変更、<xref:System.Windows.Media.Matrix.OffsetX%2A>と<xref:System.Windows.Media.Matrix.OffsetY%2A>プロパティ、ボタンの位置を変更できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f91a8-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2.  <span data-ttu-id="f91a8-112">2 番目をアニメーション化<xref:System.Windows.Media.Matrix>1.0 秒です。</span><span class="sxs-lookup"><span data-stu-id="f91a8-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="f91a8-113">ボタンは、ボタンが不要になった傾斜または拡張されていて、別の位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="f91a8-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3.  <span data-ttu-id="f91a8-114">アニメーションを無限に繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="f91a8-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f91a8-115">派生するフレームのキー、<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>オブジェクト作成の値の間の急激なジャンプであり、アニメーションの動きがスムーズでないです。</span><span class="sxs-lookup"><span data-stu-id="f91a8-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f91a8-116">サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f91a8-116">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91a8-117">参照</span><span class="sxs-lookup"><span data-stu-id="f91a8-117">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [<span data-ttu-id="f91a8-118">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="f91a8-118">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="f91a8-119">キー フレームに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="f91a8-119">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
