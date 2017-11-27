---
title: "方法 : 要素をスケーリングする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23b3086452526e804bfdbe50bb0c134f33158f5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="fd4c8-102">方法 : 要素をスケーリングする</span><span class="sxs-lookup"><span data-stu-id="fd4c8-102">How to: Scale an Element</span></span>
<span data-ttu-id="fd4c8-103">この例を使用する方法を示しています、<xref:System.Windows.Media.ScaleTransform>要素のスケールを設定します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="fd4c8-104">使用して、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>と<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>プロパティを指定する場合の係数して要素のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="fd4c8-105">たとえば、 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 1.5 の値が元の幅の 150% に要素を拡大します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="fd4c8-106">A<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>値 0.5 は 50%、要素の高さを縮小します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="fd4c8-107">使用して、<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>プロパティをスケール操作の中心であるポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="fd4c8-108">既定では、<xref:System.Windows.Media.ScaleTransform>四角形の左上隅に対応するポイント (0, 0) で中央揃えされます。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="fd4c8-109">これは、要素の移動とも適用すると、サイズが大きくなるように見えるので、<xref:System.Windows.Media.Transform>オブジェクトが存在する座標空間を変更します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="fd4c8-110">次の例では、 <xref:System.Windows.Media.ScaleTransform> 50 での 50 のサイズを 2 倍に<xref:System.Windows.Shapes.Rectangle>です。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="fd4c8-111"><xref:System.Windows.Media.ScaleTransform>両方の値を 0 (既定値) を持つ<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>です。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd4c8-112">例</span><span class="sxs-lookup"><span data-stu-id="fd4c8-112">Example</span></span>  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="fd4c8-113">通常、設定<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>のスケールが設定されるオブジェクトの中心に: (<xref:System.Windows.FrameworkElement.Width%2A>/2、  <xref:System.Windows.FrameworkElement.Height%2A> /2)。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="fd4c8-114">次の例に示します別<xref:System.Windows.Shapes.Rectangle>が 2 倍の大きさです。 ただし、この<xref:System.Windows.Media.ScaleTransform>両方に対して 25 の値を持つ<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>、四角形の中心に対応します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="fd4c8-115">次の図は、2 つの差<xref:System.Windows.Media.ScaleTransform>操作します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="fd4c8-116">点線は、拡大/縮小する前の四角形のサイズと位置を示しています。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="fd4c8-117">![中心点が異なる 2 倍のスケール](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="fd4c8-117">![2x scales with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="fd4c8-118">2 つの ScaleTransform 操作では、ScaleX と ScaleY の値は同じですが、中心点が異なっています。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="fd4c8-119">完全なサンプルについては、「[2-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4c8-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd4c8-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="fd4c8-121">変換の概要</span><span class="sxs-lookup"><span data-stu-id="fd4c8-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="fd4c8-122">方法トピック</span><span class="sxs-lookup"><span data-stu-id="fd4c8-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
