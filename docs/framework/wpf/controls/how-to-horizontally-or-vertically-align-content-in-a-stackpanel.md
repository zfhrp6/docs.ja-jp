---
title: "方法 : StackPanel にコンテンツを水平方向または垂直方向に配置する"
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
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad3252b249c716d59b72a6c5af7bd96f2d058126
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>方法 : StackPanel にコンテンツを水平方向または垂直方向に配置する
この例では、調整、<xref:System.Windows.Controls.StackPanel.Orientation%2A>内のコンテンツの<xref:System.Windows.Controls.StackPanel>を調整する方法と、要素、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>子コンテンツのです。  
  
## <a name="example"></a>例  
 次の例では、3 つが作成されます<xref:System.Windows.Controls.ListBox>内の要素[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。 各<xref:System.Windows.Controls.ListBox>の有効な値を表す、 <xref:System.Windows.Controls.StackPanel.Orientation%2A>、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>のプロパティ、<xref:System.Windows.Controls.StackPanel>です。 ユーザーがのいずれかの値を選択すると、<xref:System.Windows.Controls.ListBox>要素、関連付けられたプロパティの<xref:System.Windows.Controls.StackPanel>とその子<xref:System.Windows.Controls.Button>要素を変更します。  
  
 [!code-xaml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 次の分離コード ファイルに関連付けられているイベントに変更を定義する、<xref:System.Windows.Controls.ListBox>選択範囲が変更されます。 <xref:System.Windows.Controls.StackPanel>によって識別される、 <xref:System.Windows.FrameworkElement.Name%2A> `sp1`です。  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
