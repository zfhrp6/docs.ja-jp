---
title: '方法 : アニメーションをテキストに適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56a12ca915cc320619a094df38d118eabf202734
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545439"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="32a86-102">方法 : アニメーションをテキストに適用する</span><span class="sxs-lookup"><span data-stu-id="32a86-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="32a86-103">アニメーションを利用すると、アプリケーションのテキストの表示方法や見た目を変えることができます。</span><span class="sxs-lookup"><span data-stu-id="32a86-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="32a86-104">次の例では、アニメーションの別の種類を使用して、内のテキストの表示には影響を<xref:System.Windows.Controls.TextBlock>コントロール。</span><span class="sxs-lookup"><span data-stu-id="32a86-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32a86-105">例</span><span class="sxs-lookup"><span data-stu-id="32a86-105">Example</span></span>  
 <span data-ttu-id="32a86-106">次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>テキスト ブロックの幅をアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="32a86-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="32a86-107">幅の値が 10 秒間、テキスト ブロックの幅から 0 に変化します。その後、幅の値を戻します。</span><span class="sxs-lookup"><span data-stu-id="32a86-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="32a86-108">この種類のアニメーションでワイプ効果を作ります。</span><span class="sxs-lookup"><span data-stu-id="32a86-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="32a86-109">次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>テキスト ブロックの不透明度をアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="32a86-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="32a86-110">不透明度の値が 5 秒間、1.0 から 0 に変化し、その後、不透明度の値を戻します。</span><span class="sxs-lookup"><span data-stu-id="32a86-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="32a86-111">次の図の効果を示しています、<xref:System.Windows.Controls.TextBlock>コントロールからの不透明度を変更する`1.00`に`0.00`によって定義された 5 秒間隔の間に、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>です。</span><span class="sxs-lookup"><span data-stu-id="32a86-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 <span data-ttu-id="32a86-112">![テキストの不透明度を 1.00 から 0.00 に変更する](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span><span class="sxs-lookup"><span data-stu-id="32a86-112">![Text changing opacity from 1.00 to 0.00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span></span>  
<span data-ttu-id="32a86-113">テキストの不透明度が 1.00 から 0.00 に変化します</span><span class="sxs-lookup"><span data-stu-id="32a86-113">Text Opacity changing from 1.00 to 0.00</span></span>  
  
 <span data-ttu-id="32a86-114">次の例では、<xref:System.Windows.Media.Animation.ColorAnimation>テキスト ブロックの前景色をアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="32a86-114">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="32a86-115">前景色の値が 5 秒間、ある色から別の色に変化し、その後、色の値を戻します。</span><span class="sxs-lookup"><span data-stu-id="32a86-115">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="32a86-116">次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>テキスト ブロックを回転します。</span><span class="sxs-lookup"><span data-stu-id="32a86-116">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="32a86-117">テキスト ブロックは 20 秒間、完全な回転を行い、その後、回転を引き続き繰り返します。</span><span class="sxs-lookup"><span data-stu-id="32a86-117">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="32a86-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="32a86-118">See Also</span></span>  
 [<span data-ttu-id="32a86-119">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="32a86-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
