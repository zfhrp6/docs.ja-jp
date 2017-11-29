---
title: "方法 : イベントの発生時に要素に変換を適用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 58ef8c008eea4c10228ebb10ceadb5806dfbc0f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="43b6b-102">方法 : イベントの発生時に要素に変換を適用する</span><span class="sxs-lookup"><span data-stu-id="43b6b-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="43b6b-103">この例に適用する方法を示しています、<xref:System.Windows.Media.ScaleTransform>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="43b6b-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="43b6b-104">ここで示される概念は、他の種類の変換を適用する場合に使用するものと同じです。</span><span class="sxs-lookup"><span data-stu-id="43b6b-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="43b6b-105">使用可能な種類の変換の詳細については、次を参照してください。、<xref:System.Windows.Media.Transform>クラスまたは[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="43b6b-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
 <span data-ttu-id="43b6b-106">要素に変換を適用するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="43b6b-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
-   <span data-ttu-id="43b6b-107">操作を行う場合*いない*にレイアウトに影響を使用して変換する、<xref:System.Windows.UIElement.RenderTransform%2A>要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="43b6b-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
-   <span data-ttu-id="43b6b-108">レイアウトに影響する変換行う場合を使用して、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="43b6b-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="43b6b-109">次の例に適用されます、<xref:System.Windows.Media.ScaleTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>ボタンのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="43b6b-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="43b6b-110">ボタンの上、マウスを動かしたときに、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>と<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>のプロパティ、<xref:System.Windows.Media.ScaleTransform>に設定されている`2`、ボタンのサイズが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="43b6b-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="43b6b-111">オフ、ボタン、マウスを動かしたときに<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>と<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>に設定されている`1`、それが原因で、元のサイズに戻るにはボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43b6b-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b6b-112">例</span><span class="sxs-lookup"><span data-stu-id="43b6b-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="43b6b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="43b6b-113">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="43b6b-114">変換の概要</span><span class="sxs-lookup"><span data-stu-id="43b6b-114">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="43b6b-115">方法トピック</span><span class="sxs-lookup"><span data-stu-id="43b6b-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="43b6b-116">ルーティング イベントの概要</span><span class="sxs-lookup"><span data-stu-id="43b6b-116">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
