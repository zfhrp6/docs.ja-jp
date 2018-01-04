---
title: "方法 : Dock の値を取得または設定する"
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
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d663acf446ee2f7a36fc2d0c8605c31a0f2a84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-or-set-a-dock-value"></a>方法 : Dock の値を取得または設定する
次の例を割り当てる方法を示しています、<xref:System.Windows.Controls.Dock>オブジェクトの値。 この例では、<xref:System.Windows.Controls.DockPanel.GetDock%2A>と<xref:System.Windows.Controls.DockPanel.SetDock%2A>のメソッド<xref:System.Windows.Controls.DockPanel>です。  
  
## <a name="example"></a>例  
 例では、インスタンスを作成する、<xref:System.Windows.Controls.TextBlock>要素、 `txt1`、し、割り当てます、<xref:System.Windows.Controls.Dock>の値`Top`を使用して、<xref:System.Windows.Controls.DockPanel.SetDock%2A>メソッドの<xref:System.Windows.Controls.DockPanel>します。 そしての値を追加、<xref:System.Windows.Controls.Dock>プロパティを<xref:System.Windows.Controls.TextBlock.Text%2A>の<xref:System.Windows.Controls.TextBlock>要素を使用して、<xref:System.Windows.Controls.DockPanel.GetDock%2A>メソッドです。 この例の最後に、追加、<xref:System.Windows.Controls.TextBlock>要素を親<xref:System.Windows.Controls.DockPanel>、`dp1`です。  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.DockPanel>  
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>  
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
