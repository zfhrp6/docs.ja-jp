---
title: "方法 : 要素のスピンを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e7dac2b1afb9d0ed385f3c25c2e30a93ea8a24f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="b7931-102">方法 : 要素のスピンを設定する</span><span class="sxs-lookup"><span data-stu-id="b7931-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="b7931-103">この例は、スピンを使用して要素を作成する方法を示しています、<xref:System.Windows.Media.RotateTransform>と<xref:System.Windows.Media.Animation.DoubleAnimation>です。</span><span class="sxs-lookup"><span data-stu-id="b7931-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="b7931-104">次の例に適用されます、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="b7931-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="b7931-105">この例では、<xref:System.Windows.Media.Animation.DoubleAnimation>アニメーション化する、<xref:System.Windows.Media.RotateTransform.Angle%2A>の<xref:System.Windows.Media.RotateTransform>です。</span><span class="sxs-lookup"><span data-stu-id="b7931-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="b7931-106">例を設定するのには、要素を回転、<xref:System.Windows.UIElement.RenderTransformOrigin%2A>点 (0.5, 0.5) する要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="b7931-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7931-107">例</span><span class="sxs-lookup"><span data-stu-id="b7931-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="b7931-108">例については変換が含まれている完全なサンプルは、次を参照してください。 [2-d 変換サンプル](http://go.microsoft.com/fwlink/?LinkID=158252)です。</span><span class="sxs-lookup"><span data-stu-id="b7931-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7931-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7931-109">See Also</span></span>  
 [<span data-ttu-id="b7931-110">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="b7931-110">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="b7931-111">変換の概要</span><span class="sxs-lookup"><span data-stu-id="b7931-111">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
