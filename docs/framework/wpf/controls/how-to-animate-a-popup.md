---
title: "方法 : ポップアップをアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd79b29849510f40034dd0e2f1d9668c9b742929
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="b39c7-102">方法 : ポップアップをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="b39c7-102">How to: Animate a Popup</span></span>
<span data-ttu-id="b39c7-103">この例は、アニメーション化する 2 つの方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>コントロール。</span><span class="sxs-lookup"><span data-stu-id="b39c7-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b39c7-104">例</span><span class="sxs-lookup"><span data-stu-id="b39c7-104">Example</span></span>  
 <span data-ttu-id="b39c7-105">次の例のセット、<xref:System.Windows.Controls.Primitives.PopupAnimation>プロパティの値を<xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>、これにより、 <xref:System.Windows.Controls.Primitives.Popup> "スライドには、する"表示されたとき。</span><span class="sxs-lookup"><span data-stu-id="b39c7-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="b39c7-106">回転するために、 <xref:System.Windows.Controls.Primitives.Popup>、この例では、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>プロパティを<xref:System.Windows.Controls.Canvas>の子要素では、<xref:System.Windows.Controls.Primitives.Popup>です。</span><span class="sxs-lookup"><span data-stu-id="b39c7-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="b39c7-107">トランス フォームが正常に動作するには、例を設定する必要があります、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="b39c7-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="b39c7-108">さらに、<xref:System.Windows.FrameworkElement.Margin%2A>上、<xref:System.Windows.Controls.Canvas>コンテンツに必要な領域を指定する必要があります、<xref:System.Windows.Controls.Primitives.Popup>に回転させます。</span><span class="sxs-lookup"><span data-stu-id="b39c7-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="b39c7-109">次の例に示す方法、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントが発生時に、<xref:System.Windows.Controls.Button>がクリックすると、トリガー、<xref:System.Windows.Media.Animation.Storyboard>アニメーションを開始します。</span><span class="sxs-lookup"><span data-stu-id="b39c7-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="b39c7-110">参照</span><span class="sxs-lookup"><span data-stu-id="b39c7-110">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="b39c7-111">方法トピック</span><span class="sxs-lookup"><span data-stu-id="b39c7-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [<span data-ttu-id="b39c7-112">ポップアップの概要</span><span class="sxs-lookup"><span data-stu-id="b39c7-112">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
