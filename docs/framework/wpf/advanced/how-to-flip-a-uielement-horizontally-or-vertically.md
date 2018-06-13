---
title: '方法 : UIElement を左右または上下に反転させる'
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 89dcf668f1fe361480dabdab227a35ea40c344a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544396"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a><span data-ttu-id="f6f57-102">方法 : UIElement を左右または上下に反転させる</span><span class="sxs-lookup"><span data-stu-id="f6f57-102">How to: Flip a UIElement Horizontally or Vertically</span></span>
<span data-ttu-id="f6f57-103">この例を使用する方法を示しています、<xref:System.Windows.Media.ScaleTransform>反転するのには、<xref:System.Windows.UIElement>水平方向または垂直方向にします。</span><span class="sxs-lookup"><span data-stu-id="f6f57-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to flip a <xref:System.Windows.UIElement> horizontally or vertically.</span></span> <span data-ttu-id="f6f57-104">この例では、<xref:System.Windows.Controls.Button>コントロール (の型<xref:System.Windows.UIElement>) を適用して反転、<xref:System.Windows.Media.ScaleTransform>にその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f6f57-104">In this example, a <xref:System.Windows.Controls.Button> control (a type of <xref:System.Windows.UIElement>) is flipped by applying a <xref:System.Windows.Media.ScaleTransform> to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f57-105">例</span><span class="sxs-lookup"><span data-stu-id="f6f57-105">Example</span></span>  
 <span data-ttu-id="f6f57-106">次の図は、反転するボタンを示しています。</span><span class="sxs-lookup"><span data-stu-id="f6f57-106">The following illustration shows the button to flip.</span></span>  
  
 <span data-ttu-id="f6f57-107">![変換のないボタン](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span><span class="sxs-lookup"><span data-stu-id="f6f57-107">![A button with no transform](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span></span>  
<span data-ttu-id="f6f57-108">反転する ui 要素</span><span class="sxs-lookup"><span data-stu-id="f6f57-108">The UIElement to flip</span></span>  
  
 <span data-ttu-id="f6f57-109">ボタンを作成するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6f57-109">The following shows the code that creates the button.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a><span data-ttu-id="f6f57-110">例</span><span class="sxs-lookup"><span data-stu-id="f6f57-110">Example</span></span>  
 <span data-ttu-id="f6f57-111">ボタンを水平方向に反転 を作成、<xref:System.Windows.Media.ScaleTransform>設定とその<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>プロパティを-1 にします。</span><span class="sxs-lookup"><span data-stu-id="f6f57-111">To flip the button horizontally, create a <xref:System.Windows.Media.ScaleTransform> and set its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property to -1.</span></span> <span data-ttu-id="f6f57-112">適用、 <xref:System.Windows.Media.ScaleTransform>  ボタンの<xref:System.Windows.UIElement.RenderTransform%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f6f57-112">Apply the <xref:System.Windows.Media.ScaleTransform> to the button's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 <span data-ttu-id="f6f57-113">![水平方向に反転されるボタン&#40;0, 0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span><span class="sxs-lookup"><span data-stu-id="f6f57-113">![A button flipped horizontally about &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span></span>  
<span data-ttu-id="f6f57-114">ScaleTransform を適用した後、ボタン</span><span class="sxs-lookup"><span data-stu-id="f6f57-114">The button after applying the ScaleTransform</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f57-115">例</span><span class="sxs-lookup"><span data-stu-id="f6f57-115">Example</span></span>  
 <span data-ttu-id="f6f57-116">前の図からわかるように、ボタンは反転したもに移動されました。</span><span class="sxs-lookup"><span data-stu-id="f6f57-116">As you can see from the previous illustration, the button was flipped, but it was also moved.</span></span> <span data-ttu-id="f6f57-117">ボタンは、左上隅から反転したためです。</span><span class="sxs-lookup"><span data-stu-id="f6f57-117">That's because the button was flipped from its top left corner.</span></span> <span data-ttu-id="f6f57-118">適用する場所で、ボタンを反転するのには、<xref:System.Windows.Media.ScaleTransform>できません、上隅にある、中央にします。</span><span class="sxs-lookup"><span data-stu-id="f6f57-118">To flip the button in place, you want to apply the <xref:System.Windows.Media.ScaleTransform> to its center, not its corner.</span></span> <span data-ttu-id="f6f57-119">適用する簡単な方法、<xref:System.Windows.Media.ScaleTransform>ボタン センターでボタンの設定には<xref:System.Windows.UIElement.RenderTransformOrigin%2A>プロパティを 0.5 0.5 です。</span><span class="sxs-lookup"><span data-stu-id="f6f57-119">An easy way to apply the <xref:System.Windows.Media.ScaleTransform> to the buttons center is to set the button's <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to 0.5, 0.5.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 <span data-ttu-id="f6f57-120">![中心の周り水平方向に反転されるボタン](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="f6f57-120">![A button flipped horizontally about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span></span>  
<span data-ttu-id="f6f57-121">0.5 の RenderTransformOrigin ボタン 0.5</span><span class="sxs-lookup"><span data-stu-id="f6f57-121">The button with a RenderTransformOrigin of 0.5, 0.5</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f57-122">例</span><span class="sxs-lookup"><span data-stu-id="f6f57-122">Example</span></span>  
 <span data-ttu-id="f6f57-123">ボタンを垂直方向に反転するには設定、<xref:System.Windows.Media.ScaleTransform>オブジェクトの<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>プロパティの代わりにその<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f6f57-123">To flip the button vertically, set the <xref:System.Windows.Media.ScaleTransform> object's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> property instead of its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 <span data-ttu-id="f6f57-124">![中心の周り垂直方向に反転されるボタン](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="f6f57-124">![A button flipped vertically about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span></span>  
<span data-ttu-id="f6f57-125">垂直方向に反転されたボタン</span><span class="sxs-lookup"><span data-stu-id="f6f57-125">The vertically flipped button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f57-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6f57-126">See Also</span></span>  
 [<span data-ttu-id="f6f57-127">変換の概要</span><span class="sxs-lookup"><span data-stu-id="f6f57-127">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
