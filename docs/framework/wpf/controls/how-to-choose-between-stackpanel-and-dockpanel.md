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
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>方法 : StackPanel または DockPanel を選択する
この例の使用を選択する方法を示しています、<xref:System.Windows.Controls.StackPanel>または<xref:System.Windows.Controls.DockPanel>内のコンテンツをスタックする場合、<xref:System.Windows.Controls.Panel>です。  
  
## <a name="example"></a>例  
 いずれかを使用できますが、<xref:System.Windows.Controls.DockPanel>または<xref:System.Windows.Controls.StackPanel>に子要素をスタックには、2 つのコントロールは常に結果が得られない同じです。 たとえば、子要素を配置する順序に影響する可能性内の子要素のサイズ、<xref:System.Windows.Controls.DockPanel>ではなく、<xref:System.Windows.Controls.StackPanel>です。 この動作の違いが発生した<xref:System.Windows.Controls.StackPanel>でスタックの方向にメジャー <xref:System.Double>.<xref:System.Double.PositiveInfinity>。 ただし、<xref:System.Windows.Controls.DockPanel>のみ利用可能なサイズを測定します。  
  
 次の例では、この重要な違い<xref:System.Windows.Controls.DockPanel>と<xref:System.Windows.Controls.StackPanel>です。  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
