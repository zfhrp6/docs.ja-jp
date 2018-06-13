---
title: '方法 : StackPanel または DockPanel を選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: c9bfb8d29051a9cfa61d3fcb93b8bb9a68d14e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551935"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="ce9ce-102">方法 : StackPanel または DockPanel を選択する</span><span class="sxs-lookup"><span data-stu-id="ce9ce-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="ce9ce-103">この例の使用を選択する方法を示しています、<xref:System.Windows.Controls.StackPanel>または<xref:System.Windows.Controls.DockPanel>内のコンテンツをスタックする場合、<xref:System.Windows.Controls.Panel>です。</span><span class="sxs-lookup"><span data-stu-id="ce9ce-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce9ce-104">例</span><span class="sxs-lookup"><span data-stu-id="ce9ce-104">Example</span></span>  
 <span data-ttu-id="ce9ce-105">いずれかを使用できますが、<xref:System.Windows.Controls.DockPanel>または<xref:System.Windows.Controls.StackPanel>に子要素をスタックには、2 つのコントロールは常に結果が得られない同じです。</span><span class="sxs-lookup"><span data-stu-id="ce9ce-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="ce9ce-106">たとえば、子要素を配置する順序に影響する可能性内の子要素のサイズ、<xref:System.Windows.Controls.DockPanel>ではなく、<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="ce9ce-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="ce9ce-107">この動作の違いが発生した<xref:System.Windows.Controls.StackPanel>でスタックの方向にメジャー <xref:System.Double>.<xref:System.Double.PositiveInfinity>。 ただし、<xref:System.Windows.Controls.DockPanel>のみ利用可能なサイズを測定します。</span><span class="sxs-lookup"><span data-stu-id="ce9ce-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at <xref:System.Double>.<xref:System.Double.PositiveInfinity>; however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>  
  
 <span data-ttu-id="ce9ce-108">次の例では、この重要な違い<xref:System.Windows.Controls.DockPanel>と<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="ce9ce-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ce9ce-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce9ce-109">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [<span data-ttu-id="ce9ce-110">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="ce9ce-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
