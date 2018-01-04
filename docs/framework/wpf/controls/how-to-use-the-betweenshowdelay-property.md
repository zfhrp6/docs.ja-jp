---
title: "方法 : BetweenShowDelay プロパティを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfd4bb4c9e26361e5b8f573d06449b090497acd6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>方法 : BetweenShowDelay プロパティを使用する
使用するこの例に示します、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>ツールヒントが簡単に表示されるように時刻プロパティ — がほとんどまたはまったくない遅れて — ときに、ユーザー、マウスのポインター 1 つのツールヒントから直接別に移動します。  
  
## <a name="example"></a>例  
 次の例で、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>プロパティが 1 秒 (1000 ミリ秒) に設定され、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>両方のツールヒントに 2 秒 (2000 ミリ秒) に設定されている<xref:System.Windows.Shapes.Ellipse>コントロール。 省略記号のいずれかのツールヒントを表示し、マウス ポインターを移動別の楕円に一時停止、2 秒以内にしていて、2 番目の楕円のツールヒントがすぐに表示されます。  
  
 次のシナリオのいずれかで、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>適用、それが原因で表示される前に、1 秒間待機する 2 番目の楕円のヒント。  
  
-   移動に要した時間が 2 番目のボタンが 2 秒より長くします。  
  
-   ツールヒントが最初の楕円の時間間隔の先頭に表示されていない場合。  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [方法トピック](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [ToolTip の概要](../../../../docs/framework/wpf/controls/tooltip-overview.md)
