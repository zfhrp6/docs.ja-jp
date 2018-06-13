---
title: '方法 : DockPanel 要素を使用して領域を分割する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: 6b10fbcd14236f9259dc5772e7f8763c1602d0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553885"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>方法 : DockPanel 要素を使用して領域を分割する
次の例では、単純な[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]framework を使用して、<xref:System.Windows.Controls.DockPanel>要素。 <xref:System.Windows.Controls.DockPanel>子要素に使用可能な領域をパーティション分割します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Windows.Controls.DockPanel.Dock%2A>プロパティと同一の 2 つをドッキングするのには、添付プロパティは<xref:System.Windows.Controls.Border>要素で、<xref:System.Windows.Controls.Dock.Top>パーティション分割された領域のです。 3 番目<xref:System.Windows.Controls.Border>に要素がドッキングされている、 <xref:System.Windows.Controls.Dock.Left>、その幅 200 ピクセルに設定します。 4 つ目の<xref:System.Windows.Controls.Border>にドッキングされて、<xref:System.Windows.Controls.Dock.Bottom>画面。 最後の<xref:System.Windows.Controls.Border>要素は、残りの領域を自動的に入力します。  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  既定では、最後の子、<xref:System.Windows.Controls.DockPanel>要素は、残りの未割り当て領域を塗りつぶします。 この動作にしない場合は、`LastChildFill="False"`を設定します。  
  
 コンパイル済みのアプリケーションでは、次のような新しい UI を生成します。  
  
 ![一般的な DockPanel シナリオ。] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.DockPanel>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
