---
title: '方法 : ポップアップをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: 05b84eea7fe983340ebb8c5cdb20ff39eb2f0858
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553755"
---
# <a name="how-to-animate-a-popup"></a>方法 : ポップアップをアニメーション化する
この例は、アニメーション化する 2 つの方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>コントロール。  
  
## <a name="example"></a>例  
 次の例のセット、<xref:System.Windows.Controls.Primitives.PopupAnimation>プロパティの値を<xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>、これにより、 <xref:System.Windows.Controls.Primitives.Popup> "スライドには、する"表示されたとき。  
  
 回転するために、 <xref:System.Windows.Controls.Primitives.Popup>、この例では、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>プロパティを<xref:System.Windows.Controls.Canvas>の子要素では、<xref:System.Windows.Controls.Primitives.Popup>です。  
  
 トランス フォームが正常に動作するには、例を設定する必要があります、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`です。 さらに、<xref:System.Windows.FrameworkElement.Margin%2A>上、<xref:System.Windows.Controls.Canvas>コンテンツに必要な領域を指定する必要があります、<xref:System.Windows.Controls.Primitives.Popup>に回転させます。  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 次の例に示す方法、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントが発生時に、<xref:System.Windows.Controls.Button>がクリックすると、トリガー、<xref:System.Windows.Media.Animation.Storyboard>アニメーションを開始します。  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [方法トピック](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [ポップアップの概要](../../../../docs/framework/wpf/controls/popup-overview.md)
