---
title: "方法 : DockPanel 要素を使用して領域を分割する"
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
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4adfabba76e9f6bf32e47fe4e52e42b68676bc0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="6865f-102">方法 : DockPanel 要素を使用して領域を分割する</span><span class="sxs-lookup"><span data-stu-id="6865f-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="6865f-103">次の例では、単純な[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]framework を使用して、<xref:System.Windows.Controls.DockPanel>要素。</span><span class="sxs-lookup"><span data-stu-id="6865f-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="6865f-104"><xref:System.Windows.Controls.DockPanel>子要素に使用可能な領域をパーティション分割します。</span><span class="sxs-lookup"><span data-stu-id="6865f-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6865f-105">例</span><span class="sxs-lookup"><span data-stu-id="6865f-105">Example</span></span>  
 <span data-ttu-id="6865f-106">この例では、<xref:System.Windows.Controls.DockPanel.Dock%2A>プロパティと同一の 2 つをドッキングするのには、添付プロパティは<xref:System.Windows.Controls.Border>要素で、<xref:System.Windows.Controls.Dock.Top>パーティション分割された領域のです。</span><span class="sxs-lookup"><span data-stu-id="6865f-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="6865f-107">3 番目<xref:System.Windows.Controls.Border>に要素がドッキングされている、 <xref:System.Windows.Controls.Dock.Left>、その幅 200 ピクセルに設定します。</span><span class="sxs-lookup"><span data-stu-id="6865f-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="6865f-108">4 つ目の<xref:System.Windows.Controls.Border>にドッキングされて、<xref:System.Windows.Controls.Dock.Bottom>画面。</span><span class="sxs-lookup"><span data-stu-id="6865f-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="6865f-109">最後の<xref:System.Windows.Controls.Border>要素は、残りの領域を自動的に入力します。</span><span class="sxs-lookup"><span data-stu-id="6865f-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="6865f-110">既定では、最後の子、<xref:System.Windows.Controls.DockPanel>要素は、残りの未割り当て領域を塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="6865f-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="6865f-111">この動作にしない場合は、`LastChildFill="False"`を設定します。</span><span class="sxs-lookup"><span data-stu-id="6865f-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="6865f-112">コンパイル済みのアプリケーションでは、次のような新しい UI を生成します。</span><span class="sxs-lookup"><span data-stu-id="6865f-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="6865f-113">![一般的な DockPanel シナリオ。] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="6865f-113">![A typical DockPanel scenario.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6865f-114">参照</span><span class="sxs-lookup"><span data-stu-id="6865f-114">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 [<span data-ttu-id="6865f-115">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="6865f-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
