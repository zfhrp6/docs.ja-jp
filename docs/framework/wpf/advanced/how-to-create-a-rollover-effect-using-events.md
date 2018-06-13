---
title: '方法 : イベントを使用してロールオーバー効果を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: d458d87586614093b35fcd73969dea04fe620351
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543011"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>方法 : イベントを使用してロールオーバー効果を作成する
この例では、マウス ポインターが要素で占有される領域に出入りとして要素の色を変更する方法を示します。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルと分離コード ファイル。  
  
> [!NOTE]
>  この例は、イベントを使用する方法を示しますが、これと同じ効果を実現するために推奨される方法を使用する、<xref:System.Windows.Trigger>スタイルでします。 詳しくは、「 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]から構成されるユーザー インターフェイスを作成<xref:System.Windows.Controls.Border>の周囲、 <xref:System.Windows.Controls.TextBlock>、アタッチ、<xref:System.Windows.Input.Mouse.MouseEnter>と<xref:System.Windows.UIElement.MouseLeave>イベント ハンドラーを<xref:System.Windows.Controls.Border>です。  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 次のコードを作成、<xref:System.Windows.UIElement.MouseEnter>と<xref:System.Windows.UIElement.MouseLeave>イベント ハンドラー。  マウス ポインターが入ったとき、<xref:System.Windows.Controls.Border>の背景、<xref:System.Windows.Controls.Border>が赤に変更します。  マウス ポインターを離れるときに、<xref:System.Windows.Controls.Border>の背景、<xref:System.Windows.Controls.Border>白に変更します。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
