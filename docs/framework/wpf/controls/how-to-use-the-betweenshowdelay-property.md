---
title: '方法 : BetweenShowDelay プロパティを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 7d48fb859ec6d37abd2490bc718d58cbdaa67f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552715"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="1ab44-102">方法 : BetweenShowDelay プロパティを使用する</span><span class="sxs-lookup"><span data-stu-id="1ab44-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="1ab44-103">使用するこの例に示します、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>ツールヒントが簡単に表示されるように時刻プロパティ — がほとんどまたはまったくない遅れて — ときに、ユーザー、マウスのポインター 1 つのツールヒントから直接別に移動します。</span><span class="sxs-lookup"><span data-stu-id="1ab44-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ab44-104">例</span><span class="sxs-lookup"><span data-stu-id="1ab44-104">Example</span></span>  
 <span data-ttu-id="1ab44-105">次の例で、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>プロパティが 1 秒 (1000 ミリ秒) に設定され、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>両方のツールヒントに 2 秒 (2000 ミリ秒) に設定されている<xref:System.Windows.Shapes.Ellipse>コントロール。</span><span class="sxs-lookup"><span data-stu-id="1ab44-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="1ab44-106">省略記号のいずれかのツールヒントを表示し、マウス ポインターを移動別の楕円に一時停止、2 秒以内にしていて、2 番目の楕円のツールヒントがすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ab44-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="1ab44-107">次のシナリオのいずれかで、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>適用、それが原因で表示される前に、1 秒間待機する 2 番目の楕円のヒント。</span><span class="sxs-lookup"><span data-stu-id="1ab44-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="1ab44-108">移動に要した時間が 2 番目のボタンが 2 秒より長くします。</span><span class="sxs-lookup"><span data-stu-id="1ab44-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="1ab44-109">ツールヒントが最初の楕円の時間間隔の先頭に表示されていない場合。</span><span class="sxs-lookup"><span data-stu-id="1ab44-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="1ab44-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ab44-110">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="1ab44-111">方法トピック</span><span class="sxs-lookup"><span data-stu-id="1ab44-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="1ab44-112">ToolTip の概要</span><span class="sxs-lookup"><span data-stu-id="1ab44-112">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
