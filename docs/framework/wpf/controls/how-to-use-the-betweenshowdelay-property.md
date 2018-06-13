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
# <a name="how-to-use-the-betweenshowdelay-property"></a>方法 : BetweenShowDelay プロパティを使用する
使用するこの例に示します、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>ツールヒントが簡単に表示されるように時刻プロパティ — がほとんどまたはまったくない遅れて — ときに、ユーザー、マウスのポインター 1 つのツールヒントから直接別に移動します。  
  
## <a name="example"></a>例  
 次の例で、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>プロパティが 1 秒 (1000 ミリ秒) に設定され、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>両方のツールヒントに 2 秒 (2000 ミリ秒) に設定されている<xref:System.Windows.Shapes.Ellipse>コントロール。 省略記号のいずれかのツールヒントを表示し、マウス ポインターを移動別の楕円に一時停止、2 秒以内にしていて、2 番目の楕円のツールヒントがすぐに表示されます。  
  
 次のシナリオのいずれかで、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>適用、それが原因で表示される前に、1 秒間待機する 2 番目の楕円のヒント。  
  
-   移動に要した時間が 2 番目のボタンが 2 秒より長くします。  
  
-   ツールヒントが最初の楕円の時間間隔の先頭に表示されていない場合。  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [方法トピック](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [ToolTip の概要](../../../../docs/framework/wpf/controls/tooltip-overview.md)
